# Architecture of a visual paper

A private source repository holds the pinned paper, the content, the audit trail and
the tooling; a build turns it into a static site. Nothing runs on a server.

## Repository layout

```
<project>/
  PLAN.md            plan of record: locked decisions, controls, phases, change log
  SOURCE.lock        paper repo + commit, Lean repo + commit, sha256 of every pinned file
  source/            pinned paper: main .tex, macro files, compiled .aux and .bbl,
                     CORRESPONDENCE.md from the Lean repo, pinned external sources
  content/
    site.yaml        title, authors, year, arxiv_id (null until posted), public_url, lean_repo
    graph/<sec>.yaml section and subsection fragments (titles, summaries, ideas, children)
    nodes/<id>.yaml  one file per result node (schema below)
    notation.yaml    one entry per notation macro
    figures/<id>.yaml figure specs (claims with cites) and status
    background/      background nodes for facts taken from cited papers (optional tier)
    external/        citation maps for a cited earlier paper (optional)
    lean-extra.yaml  hand matches for Lean rows that name a paper item only in words
  audit/             packets, verdicts, ledger.json, stale.json
  schemas/           JSON Schemas for every content kind, the ledger and verdicts
  scripts/           extract, sync_source, build, build_preview, check_*, audit tooling
  site/              app (HTML/CSS/JS), macros.json, graph and figure modules
  tasks/             agent briefs;   reports/  agent reports and author-facing notes
  test/              unit and integration tests (node --test), fixtures
  dist/, dist-preview/, generated/   build outputs (gitignored)
```

Keep secrets such as the canary key in a directory outside the repository.

## Pipeline

1. **Extract** (`extract`): parse the TeX into `generated/span-index.json` — sections,
   subsections and paragraphs with spans; theorem-like environments; proofs and the
   statement each proves (bracket `[Proof of Theorem~\ref{..}]` or adjacency); labels
   with numbers from the `.aux`; the `\ref`/`\eqref` graph; citations with locators;
   bibliography from the `.bbl`; macro definitions. Make it comment-aware
   (a commented-out `\label` produces no `\newlabel`), and read numbers only from the
   `.aux`, never by counting.
2. **Macros** (`gen_macros`): translate the paper's macro file and preamble into one
   KaTeX macro table. Review it once as an artefact.
3. **Assemble**: build the node set — top-level theorems (L0), sections (L0),
   subsections (L1), result nodes (L2) — from the span index overlaid with content
   files; resolve anchors to text; render all mathematics at build time with KaTeX; compute
   edges (see [dependency graph](dependency-graph.md)); attach notation cards, figures,
   Lean badges, citations.
4. **Build** the full site into `dist/` (one `data.json` plus the app) and, if a
   private preview host has size limits, a compact preview into `dist-preview/`
   (data split per section, fonts and figures bundled, a byte budget checked).
5. **Check** (`check`), fail-closed, in this order: schema, graph, anchors, steps,
   claims, edges, acyclicity, publish (ledger), canaries, notation, external-source
   citations, KaTeX, TeX-to-HTML, built-site claims.

## Node schema (result nodes)

```yaml
id: p.main.estimate           # the paper's label; synthetic ids use x. (x.def.local-average)
kind: theorem|proposition|lemma|definition|estimate|claim
status: draft|published
parent: ss.main.estimate      # the section/subsection box that holds it on the map
title:   {id, text, cites}     # agent-written claim
statement: {file, start, end, sha256, label?}
proof:     {file, start, end, sha256}
steps:     [{cut: {line, col}, title: claim, summary: [claim]}]   # cuts inside the proof
summary:   [claim]             # plain-language statement summary
idea:      [claim]             # proof idea
uses:      [{id, origin: ref|added, cite: anchor, why}]
dropped_refs: [{id, why}]
notation_introduced: [key]
```

A claim is `{id, text, cites: [anchor | {label}]}`. Audit status is never stored in a
node; it is computed from the ledger.

## Anchors

`{file, start: {line, col}, end: {line, col}, sha256}` plus an optional `label`.
Create anchors only through the anchor library (`makeAnchor`, `anchorFromOffsets`);
never hand-edit line, column or hash. Verification recomputes the hash; a mismatch is
a stale anchor and fails the build.

## Site technology

- KaTeX for all mathematics, pre-rendered at build time, with `trust` limited to
  `\htmlClass` so that notation macros can carry a class that opens their card.
- Cytoscape.js with the dagre layout for the graph; see
  [site and launch](site-and-launch.md) for the navigation model.
- D3 over inline SVG for interactive figures, KaTeX inside SVG `foreignObject` for
  their labels; TikZ → SVG (lualatex + dvisvgm) for static ones.
- Playwright with headless Chromium for smoke tests and screenshots.
- Plain static files: GitHub Pages or any static host; a `.nojekyll` file on Pages.

## Tests worth having from day one

- Extraction counts on the real source (labels, refs, sections, citations), updated
  deliberately when the paper changes.
- An integration fixture node with real anchors that runs every check.
- The anchor, step-concatenation and claim-citation checks on synthetic fixtures.
- A sub-path serving check and a headless smoke test of figures, panels and pop-outs.
