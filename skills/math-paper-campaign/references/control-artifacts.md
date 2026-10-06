# Control artefacts

Use existing project documents when they serve these roles. Create only missing artefacts, keep them compact, and never let them become parallel manuscripts. None of this vocabulary belongs in the paper.

## Contents

1. Paper brief
2. Mathematical outline
3. Statement ledger
4. Diagnostic investigations
5. Notation and source map
6. Citation map
7. Review records
8. Structural consistency checks
9. Resume note
10. Status vocabulary

## Paper brief

Record:

- audience and intended contribution;
- principal results;
- source hierarchy: which sources are mathematical authorities and which are only evidence; for Route B, the named checked revision and the exact scope of its check, alongside the current manuscript revision;
- canonical manuscript and delivery format (for example, whether delivery requires one TeX file);
- style and notation authorities (by default the [house style](../../latex-math-writing/references/house-style.md)), any venue constraint, and representative pages for comparison;
- the author's voice profile when rewriting: technical vocabulary, theorem naming, paragraph rhythm, first-person usage, proof transitions, and banned development jargon;
- compilation, lint, and PDF-inspection commands;
- the permission envelope (see [shared controls](shared-controls.md#authority-and-permissions));
- authorship metadata and acknowledgements still needed;
- for a teaching or expository text, two or three questions a cold reader must answer after one reading;
- any page limit, with the measured size of the frozen definitions and statements;
- unresolved decisions, their owners, and required approvals.

Keep decisions here, not narrative progress logs. Before creating a new canonical manuscript, close every unresolved decision that could alter the model, principal statements, proof architecture, notation, result hierarchy, or delivery format. Record any deliberately deferred choice together with the route it cannot affect.

## Mathematical outline

Organise the outline by proof dependency rather than by the order in which ideas were discovered. For each section, record:

- objective;
- accepted inputs;
- planned public results;
- proof-local material;
- explicitly excluded material;
- least certain edge;
- exit test.

Use a dependency diagram when it makes the route materially clearer.

## Statement ledger

One row per public statement. Recommended fields:

| Field | Meaning |
|---|---|
| ID | Stable LaTeX label or provisional identifier |
| Kind | theorem, proposition, lemma, definition, assumption, or inline |
| Role | Exact downstream purpose, or a declared role as a principal reader-facing conclusion |
| Envelope | Permitted hypotheses, required conclusion and normalisation, constant dependencies and uniformities |
| Dependencies | Direct accepted inputs |
| Consumers | Later statements that use it |
| Source | Internal proof route or exact external citation |
| Home | Where the complete statement lives (for example the argument or a reference part) and whether the argument carries a short form at first use |
| Disposition | For a rewrite: `RETAIN`, `REWRITE`, `MERGE`, `DEMOTE TO PROSE`, `MOVE`, or `REMOVE`, with destination and affected consumers |
| Mathematics status | See the status vocabulary |
| Manuscript status | See the status vocabulary |
| Evidence | Review, check, or checkpoint supporting the statuses, bound to a revision |

Do not mark a row accepted merely because its strategy is plausible or its source compiles. Cite deferred statements by label, never by a typed number, and fix their numbering only after their homes are settled. For statements describing one jointly chosen object, record the quantifier structure and the order of construction.

## Diagnostic investigations

Attach each diagnostic note to one active ledger row. Record:

- the parent statement ID;
- the exact mathematical question;
- the proof edge, hypothesis, or contract it may change;
- the final disposition: `USED`, `REVISE`, `REJECTED`, or `OPEN`;
- the resulting ledger and dependency updates.

Keep the note bounded and outside the canonical manuscript. Do not let it create a successor task unless the parent proof requires that task.

## Notation and source map

Record:

- canonical symbols and macro spellings, and where each object is defined;
- for easily confused terms: mathematical kind, arguments, fixed and evolving parameters, units and normalisation, role, and whether an object is exact, a leading approximation, or an increment;
- every introduced, renamed, or removed symbol;
- conflicts between source papers or old drafts, and deliberate deviations with reasons;
- any accepted notation-translation map from a designated notation source (it governs presentation, never the mathematical contract).

Keep source provenance outside theorem statements unless the citation is mathematically needed there.

## Citation map

For every proposed external input, literature comparison, and external factual or result attribution:

| field | required content |
|---|---|
| present use | the exact claim needed here |
| authoritative source | bibliography key and stable source identity; primary when it supports the formulation |
| location | theorem, proposition, or lemma number, and section or page when available |
| source contract | hypotheses, quantifiers, normalisation, and conclusion |
| transport | specialisation, notation translation, scaling, geometry, or convention change |
| status | `CANDIDATE`, `QUOTED`, or `FAILED` |

## Review records

For a load-bearing packet, record only:

- the exact artefact revision and frozen contract reviewed;
- the reviewer's role and whether its context was fresh;
- blockers, major findings, and minor findings with exact locations;
- the accepted repair and its verification evidence;
- the resulting status.

Avoid praise, restated project context, and speculative successor tasks. Give findings stable IDs. Keep one compact finding-to-repair table across review rounds, and regression-check every previously closed blocker or major finding after later repairs. A review applies only to the recorded revision; reopen affected findings when the manuscript changes materially. Use this ledger for exposition findings too; do not start a second one.

## Structural consistency checks

When the paper has enough public statements that manual synchronisation is fragile, make the ledger machine-checkable. A small project-local checker with regression tests can verify, as applicable:

- agreement of result labels and environment kinds between the TeX and the ledger;
- existence of every dependency and absence of dependency cycles;
- that no accepted node depends on an open or insufficiently reviewed node;
- compatibility of mathematical and manuscript statuses;
- that every integrated public statement is registered, and every registered one is present;
- that review evidence is attached to the exact reviewed revision;
- definition closure: every operator and symbol in a public statement has a defining display in the document;
- cross-document label resolution: no `\ref` in any document (including companions) points to a removed or renamed label, and no label is defined twice when all modules are compiled together;
- a measured page table per unit, from compiled standalone drivers (pages and how full the last page is), beside its budget.

Semantic judgements (source fidelity, mathematical validity, whether a repair closes a finding) stay with human or agent review. A structural checker protects bookkeeping; it does not certify a theorem.

## Resume note

For a long campaign with agents running in parallel, keep a short resume note (for example `STATUS.md`), time-stamped and updated at each milestone: the running agents and their packets, the events being awaited, the queue, and the decisions pending with the author. Keep packets as self-contained files so that interrupted work can be relaunched verbatim.

## Status vocabulary

Adapt the names to the project, but keep these distinctions.

### Mathematical status

- `PLANNED`: role identified, envelope not yet accepted.
- `SPECIFIED`: paper-wide envelope accepted.
- `FROZEN`: exact statement accepted.
- `DRAFTED`: proof text exists but has not passed mathematical review.
- `PROVED`: the proof's author accepts it; independent review remains.
- `AUDITED`: independent mathematical review is green.
- `QUOTED`: the exact external result and its specialisation have been checked.
- `OPEN`: a required mathematical edge is unresolved.
- `REJECTED`: the statement or route is false, redundant, or unsuitable.

Only `AUDITED` and `QUOTED` may support another accepted load-bearing node. Route B starts from statements that are already `AUDITED` or `QUOTED` with frozen contracts.

### Manuscript status

- `ABSENT`: not in the canonical TeX.
- `DRAFTED`: present but not accepted as exposition.
- `INTEGRATED`: accepted in context and compiles.
- `REDUCED`: Route B Phase 1 passed: duplicates removed, every inference and use preserved.
- `ARCHITECTED`: Route B Phase 3 passed: placed in dependency order with a clear role.
- `EXPO-AUDITED`: an independent exposition review is green and its repairs are in the manuscript.
- `TYPESET-AUDITED`: the affected rendered pages have been read and accepted.

Route A moves a packet `ABSENT` → `DRAFTED` → `INTEGRATED` → `EXPO-AUDITED` → `TYPESET-AUDITED`. Route B moves it `INTEGRATED` → `REDUCED` → `ARCHITECTED` → `EXPO-AUDITED` → `TYPESET-AUDITED`. A packet entering Route B starts again at `INTEGRATED`, whatever its earlier editorial status, because Route B restructures and re-reviews the exposition; its mathematical status carries over.

Keep the two tracks separate. Compilation, elegant prose, or a successful Lean build never upgrades mathematical status; a mathematical review never certifies layout or readability. A repair that touches prose or mathematics reopens the relevant earlier status.
