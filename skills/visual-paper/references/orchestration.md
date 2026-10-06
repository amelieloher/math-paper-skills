# Orchestration

## Roles

Assign roles by capability, within whatever model policy governs the installation:

| Role | Does | Never does |
|---|---|---|
| Orchestrator | plan, schema, section map, briefs, audit packets, canaries, integration, acceptance by script, author communication | read the paper at length; overrule an auditor; write result-level content |
| Writer (strong comprehension; also the figure designer) | per-section nodes, links, step cuts, summaries, ideas, notation glosses, figure specs, background nodes, re-anchoring after revisions | audit its own output |
| Builder (mechanical) | scripts, macro table, site, figure implementation from approved specs, CSS, tests | write mathematical claims |
| Auditor (different model family) | blind audits, coverage checks, adjudication, figure build checks, citation checks | write or fix content |

One arrangement that works: writers and builders from one model family, and two or
three auditors from another, each in its own terminal session, dispatched one packet
at a time with a `DONE <packet>` sentinel; the orchestrator reads only verdict files.
Follow the installation's model policy.

### Terminal auditors: failure modes

Auditor sessions driven by keystrokes stall silently, for example when:

- an update or warning dialogue swallows the Enter (send Escape, wait for the prompt,
  then type; restart the session per packet rather than using an in-app `/new`);
- the model is at capacity ("Selected model is at capacity") and the session idles;
- the prompt is typed but never submitted.

A watcher must wait for success **or** failure, and scan every pane for these
states; do not trust a sentinel alone. Some pane text is benign: "No previous
message to edit" is the reply to the dispatcher's own Escape. Never start a second
batch while one runs, and never dispatch to a misspelled session name: it silently
spawns an extra auditor. If verdict files must be discarded, remove their ledger
entries too, or the ledger holds orphan verdicts. When every auditor has already seen
a claim (rotation exhausted), dispatch directly to one that did not dissent.

## Briefs

Each task brief (`tasks/<task>.md`) names its inputs (paths and line ranges), exact
output paths, the files it must not touch, acceptance (the scripts that must pass),
the commit rule, and a report limit (150–200 words). Agents write files; they do not
paste content back. Auditor packets list the only files the auditor may read.

## Parallel work

- One git worktree and branch per agent; merge in the orchestrator's checkout after
  reading the diff and running every check.
- **Give each worktree its own `node_modules`** (`npm ci` in the worktree). A
  worktree whose `node_modules` was a symlink to the main checkout's got committed by
  a blanket `git add -A`; merging the symlink replaced the main checkout's
  dependencies with a link to itself, and a later `npm ci` in a fresh clone emptied
  them. Stage explicit paths, ignore `node_modules` without a trailing slash, and
  never commit a symlink to a dependency directory.
- Split content work by section with disjoint write sets; split re-anchoring work by
  explicit worklists.

## Re-syncing to a revised paper

1. Re-pin the source and re-resolve anchors (exact text, then label). Treat fuzzy
   matches as suspect: after heavy edits they latch onto unrelated passages, and even
   after a one-word edit they produced spans starting or ending mid-word. Print the
   first and last characters of every moved span and remap bad ones by the old text:
   exact match first, else the old span's first and last 80 characters located
   separately.
   Compile every `.aux` (main paper and external sources) from the pinned `.tex` in a
   scratch copy. A stale `.aux` left in the paper's working tree gives the site, and
   the auditors' numbering legend, wrong theorem numbers.
2. Generate worklists of every anchor whose cited text changed, with the old text and
   the matcher's guess, by walking the old and new content trees.
3. Have writers re-anchor each item by hand, revise claims minimally where the
   paper's statement changed (keep the claim id), and report each action.
4. Remap proof-step cuts and external-citation line numbers by unique context; fix
   by hand any cut that ends up out of order.
5. Tests that pin positions, counts or hashes of the real source break on every
   re-sync. Make them derive these from the source at test time (locate by label or
   quoted text, numbers from the `.aux`, counts by scanning) and regenerate any
   committed fixtures after a sync.
   Content written on a branch before a re-sync carries anchors into the old source;
   the sync tool cannot repair them after the merge, because the source did not
   change. Relocate them by their exact old text before or right after merging.
6. Re-audit, or record an author waiver as in
   [integrity and audit](integrity-and-audit.md#practical-lessons).
7. Report to the authors: revised claims, waived claims, and paper-level issues found.

## Communicating with the authors

- Keep the plan of record's change log current; get explicit approval for any
  deviation (a new tier of content, a waiver, going public).
- Return paper-level findings as a list with line pointers: wrong section numbers in
  citations, missing references, typos, unclear scope of a hypothesis. Re-check each
  item against the current source before reporting it again; quoting an outdated
  notes file told the authors to fix items they had already fixed.
- When asked about difficulty, give a concrete estimate and the fiddly parts, then
  build only on a go-ahead.
- Verify reported UI problems by reproducing them first — vary viewport, page zoom,
  pixel ratio and scrollbars — rather than guessing a fix.
