---
name: visual-paper
description: Build an interactive, audited "visual paper" website from a mathematical LaTeX paper (optionally with a Lean formalisation) — a zoomable dependency graph of the proofs, exact statements and step-by-step proofs quoted from the source, audited summaries, clickable notation, interactive figures, Lean badges, and a public static deployment. Use when turning a finished or nearly finished paper into a companion website, re-syncing one to a revised paper, auditing its dependency links, or launching it alongside an arXiv posting.
---

# Build a Visual Paper

A visual paper is a static website that lets a reader enter a mathematical paper
through the structure of its proofs. The reader starts at a map of sections and main
theorems and clicks down to subsections, individual results, the exact statement,
a proof idea, numbered proof steps and the paper's own text for each step. Symbols
open their definitions; figures illustrate the key mechanisms; a Lean badge marks
what is formalised.

The governing rule: **the site never shows mathematics that no one checked.** Paper
text is shown only by hashed reference to the pinned source, never copied or
retyped. Every sentence an agent writes is a claim that cites the source spans it
rests on, and is audited by an independent auditor before the build will publish it.

Every rule below comes from building two such sites:
[the companion](https://scottnarmstrong.github.io/hcp-visual-paper/) to
Armstrong–Kuusi–Loher, *Homogenization at a polynomial scale in high contrast*, and
[the companion](https://amelieloher.github.io/DF-visual-paper/) to Loher–Mooney–Mouhot,
*Döblin–Fourier cancellation and kinetic Aleksandrov estimates*.

Throughout, *authors* means the paper's authors, who hold every approval gate (★);
*writers* are the agents that write the site's content (see
[orchestration](references/orchestration.md)).

## Lifecycle

Carry the project through these phases; each ends at a gate. Stop only at an author
gate (★), a genuine mathematical question, or missing authority.

0. **Brief and decisions.** Pin the source (TeX, macro files, `.aux`, `.bbl`; the Lean
   repository and commit if any). Record the locked decisions in a plan of record:
   scope (which theorems first), proof depth ("the paper's own proofs; no mathematics
   beyond the paper"), hosting (private preview now, public only on the authors'
   word), the private/public repository split, and the integrity controls. ★ Authors
   approve the plan.
1. **Foundations.** Extraction to a span index, anchors, the macro table and render
   harness, every check script, the site scaffold, a private preview. Calibrate the
   auditors with a trial packet of planted errors before any real audit.
   → [architecture](references/architecture.md), [integrity and audit](references/integrity-and-audit.md).
   ★ Authors review the look and navigation.
2. **Structure.** Section and subsection map (L0/L1), then per section: result nodes
   (including inline definitions, key labelled estimates, named claims), curated
   dependency links, proof-step cuts, summaries, proof ideas, notation entries, and
   one-line figure proposals. Audit every claim; iterate until the ledger is green.
   → [dependency graph](references/dependency-graph.md). ★ Authors review L0/L1 and a sample.
3. **Notation layer.** One entry per macro, wrapped at build time so every occurrence
   opens its definition card.
4. **Figures.** Decide with the `math-figures` skill which visuals earn their place. Writers, acting as figure designers, propose specs with citations → audited → ★ authors approve
   the list → builders implement → a different auditor checks each build against its
   spec. → [figures](references/figures.md).
5. **External inputs and Lean** (when the paper leans on an earlier paper, or has a
   formalisation). → [external sources and Lean](references/external-sources-and-lean.md).
6. **Polish and launch.** Reading mode, accessibility, sub-path safety, head
   metadata, licences, a public repository holding only the built site, and an
   arXiv watcher. → [site and launch](references/site-and-launch.md). ★ Authors choose
   the go-live moment.
7. **Maintenance.** Re-sync to each revision of the paper, re-audit or record an
   explicit author waiver, audit the dependency links end to end, redeploy.
   → [orchestration](references/orchestration.md#re-syncing-to-a-revised-paper).

## Non-negotiable controls

- **Anchors, not copies.** Content files hold `{file, start, end, sha256, label?}`
  anchors; the build extracts text from the pinned source. A changed span voids every
  verdict that depends on it.
- **Deterministic TeX.** One reviewed macro table; a harness renders every snippet
  and fails the build on any KaTeX error or unknown macro. Fix macros in the table,
  never in content.
- **Proof steps are cut points** whose pieces concatenate exactly to the proof span.
- **Every agent sentence is a cited claim**, rejected by schema if uncited, if it uses
  a symbol not in the notation table, or a numeral absent from its cited spans.
- **Independent blind audit** by a different model family, with planted errors
  (canaries) whose key lives outside the repository; fail-closed ledger bound to the
  claim and span hashes. The orchestrator never overrules an auditor on mathematics.
- **Dependency links are curated and cited**: mechanical `\ref` baseline, each drop
  justified, each addition anchored to the words that show the use.
- **Private until the authors decide.** The source repository stays private; only the
  built site is ever published.

## Working rules

- Delegate reading of the paper; agents write files and return short reports. See
  [orchestration](references/orchestration.md) for roles, briefs, worktrees and the
  failure modes met in practice.
- Verify every UI change in real headless browsers, Chromium **and** WebKit (figures
  render, no page errors, no KaTeX errors, sub-path serving), before any preview or
  deploy. Reading files and unit tests alone have shipped a site with no figures, and
  Chromium alone missed figures that Safari showed broken.
- Report paper-level problems found along the way (wrong section pointers, missing
  references, typos) to the authors as a list; do not silently paper over them on the
  site. Edit the paper only when asked.
- Keep a change log in the plan of record for every approved deviation.
