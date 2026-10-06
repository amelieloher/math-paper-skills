# Shared controls

Both routes use these controls. The documents and status names they refer to are defined in [control artefacts](control-artifacts.md).

## The mathematical contract

The accepted mathematics outranks every editorial improvement. No pass may silently change:

- hypotheses, conclusions, quantifier order, or logical strength;
- spaces, boundary conditions, normalisations, signs, exponents, endpoints, thresholds, or exceptional sets;
- constant dependencies, uniformities, measurability, or probability status;
- whether a fact is proved here, quoted from a source, heuristic, or open;
- the intended meaning of a symbol, definition, or named result.

Any such change is mathematical drift, even when it appears to weaken or simplify a statement. Follow the drift protocol below.

## Authority and permissions

Before work starts, inspect the outline or manuscript, any formalisation, the source papers, bibliography, macro file, local instructions, and build commands, and record in the brief:

- the audience, intended contribution, and deliverable;
- the principal theorem or theorems;
- which sources are mathematical authorities and which are only evidence;
- the canonical manuscript and the style and notation authorities;
- the compilation, lint, and PDF-inspection workflow;
- the permission envelope: writable files and directories, build scope, network or source access, use of reviewers and subagents, allowed parallelism, version-control checkpoints, push authority, and the treatment of old drafts.

Do not infer that an older paper is correct, complete, or stylistically reusable; treat it as a source to check. Preparing a release candidate does not authorise an external submission. Check the shared-file and repository state before editing, and synchronise without overwriting others' work.

## One manuscript, one editor

Maintain exactly one canonical manuscript and one active canonical editor. Only the editor writes the canonical TeX, and it rewrites accepted content into the paper's voice: never paste raw agent prose into the manuscript. An editor handoff records the current revision, the active packet, unresolved findings, and the voice authority before the next editor writes. Old drafts must not become competing authorities.

## Statement packets

The unit of work is one load-bearing public statement and its proof, with the definitions it immediately needs. A packet contains only:

- the frozen statement or its specification envelope;
- its accepted proof route and exact dependencies;
- the relevant source excerpts, declarations, and citation records;
- its consumers and current location;
- the preceding accepted reader-facing text and declared prerequisites;
- local notation, macros, style constraints, and the output location;
- the current findings and the acceptance test for this pass.

Two further items belong in a writing packet: a page budget equal to the measured size of its frozen inputs plus an allowance for prose, and the instruction to report, not resolve, any disagreement between the frozen statements and the text being written or rewritten.

Keep at most one load-bearing packet under canonical edit at a time. Several read-only reviewers may examine disjoint questions about it. This makes preservation of the claims checkable and stops global stylistic edits from hiding a local mathematical change.

Exception: when the mathematics is already checked and the task is extraction (writing out an existing statement surface), one packet may cover a set of statements, provided the review is set-level as well: every inference of the on-page proofs mapped to a clause, a list of the clauses those proofs use and do not use, and a clause-by-clause map against any previous version. The list of unused clauses tells you what can move to a reference part.

A definition and its immediate well-posedness sentence may share a packet. Supporting public lemmas are separate packets even when they share a subsection. A one-use calculation may stay inside its consumer's packet; a definition may accompany a packet only when it has no independent consumers.

## Drift protocol (fail-closed)

Treat any change to hypotheses, quantifier order, normalisation, exponents, thresholds, boundary conditions, source status, or constant uniformity as drift, even when the new statement is weaker. When work appears to require one:

1. stop editing the affected packet;
2. record the old and proposed contracts and the reason;
3. identify every dependent accepted statement and introduction claim;
4. route the mathematical question to the author and the appropriate mathematical review;
5. re-review every affected dependency edge, and update the dependency and source records only after acceptance;
6. reaccept and reintegrate the dependents only once the dependency graph is consistent again;
7. reopen every affected editorial status and regress earlier findings.

Reshaping a frozen statement for readability (splitting it into clauses, moving definitions into display blocks, specialising a general theorem to the construction) is drift too, even when it is meant as wording. Keep the previous checked text, require the writer to list every change of content, and review the new text clause by clause against the old one, including every consumer in companion documents. Undeclared losses, such as a condition that silently disappears, are the main risk, more than false new claims.

Do not hide drift inside a proof repair, a simplification, a specialisation, a notation clean-up, a correction from a formalisation, or a citation replacement. A Lean mismatch is valuable evidence, but it enters this protocol like any other mathematical finding. Do not promote Lean API lemmas or formalisation scaffolding into the paper unless they independently improve the reader-facing argument.

## Reviewers

Use a reviewer other than the proof's author, or a fresh context, for every load-bearing result. A subagent is the practical instrument: it starts without the drafting session's assumptions, which is what makes its objections informative. Choose reviewer models according to the installation's policy; a fresh context with exact inputs matters most.

- Give the reviewer the actual statement and proof bound to an exact revision, never an author's summary or the reasoning that produced them.
- Give it a bounded question, exact inputs, a disjoint write set if writing is needed, and an acceptance format: findings with stable IDs, evidence, severity, and the smallest repair. Reviewers do not invent successor work, alter the theorem surface, or co-edit the main TeX.
- Read a returned finding before acting on it. A reviewer can be confidently wrong about a statement it reconstructed rather than read; check the objection against the revision it cites.
- Scale review to risk. A principal theorem needs a fresh review of its dependency closure; a routine three-line lemma does not need a committee.
- After any exposition rewrite, the mathematical review covers the new text itself: classify every new explanatory sentence and every table entry as true or false, with evidence. A false heuristic sentence is a blocker, even when every formula was preserved.
- When files move under concurrent edits, reviewers name the frozen snapshot they read (with a hash manifest), and writers applying findings locate places by content, not by line number.

Useful independent roles, run concurrently on read-only packets:

- **contract reviewer:** compares old and new statements and proof edges, and checks each inference;
- **source reviewer:** checks exact citations, hypotheses, and translations;
- **architecture reviewer:** tests dependency order, consumers, statement minimality, and redundancy;
- **notation reviewer:** checks duplication and notation cost;
- **exposition reviewer:** tests cognitive granularity, voice, intuition, and deletion, using [the comprehension test](../../latex-math-writing/references/artisan-writing.md#test-comprehension-from-the-readers-text);
- **rendered reader:** inspects the compiled pages and reads linearly;
- **exposition critic** (for a long narrative or teaching text): a read-only reviewer with a defined brief, separate from the mathematical reviewers. Ask it for dispositions per file (keep, move, short form), exact short-form texts, page caps per block, and the one sentence a reader should remember per section; not for rewrites. Any proposal of the critic that touches a statement goes through mathematical review, and the frozen statement wins wherever the critic's shorthand differs.

## Checkpoints

After each accepted packet, compile the smallest target, run available consistency checks, inspect the affected PDF pages, and update the ledger. If version-control checkpoints are authorised, commit a green boundary before opening the next load-bearing packet. Do not push unless asked.

## Final audit

Bind the final audit to a named canonical revision. Then:

1. compare every theorem and definition with its frozen contract and recheck every dependency edge (a theorem-surface and dependency-closure audit);
2. verify every external input and literature comparison against its citation record;
3. sweep globally for duplicate results, definitions, notation, labels, citations, unused hypotheses, unexplained symbols, and stale forward references;
4. compile cleanly with bibliography and cross-reference checks; assess every warning and fix overfull or visibly poor material;
5. run the source-hygiene and project-specific checks;
6. have the editor or a designated fresh rendered-page reviewer inspect and accept every page at readable resolution, including page breaks, theorem placement, displays, captions, bibliography, and neighbouring prose;
7. commission a fresh linear-reader review from title through bibliography, applying the comprehension test, and regress every earlier finding to its accepted repair;
8. check title, abstract, metadata, acknowledgements, disclosures, data and code statements, and venue requirements when in scope;
9. synchronise the ledger and review records to the release-candidate revision, including who read every page.

If the author wants a single TeX file, consolidate modular sources only after the mathematics is stable, then recheck counters, labels, bibliography, macros, duplicated definitions, and layout.

Any later change touching an audited claim or its presentation reopens the affected audit and requires regression against earlier findings. The result is a release candidate: submission, upload, or other publication remains the author's decision unless explicitly requested.

## Completion test

The paper is complete only if every answer is yes:

- Is the output bound to accepted mathematical contracts, with every drift event re-reviewed and approved by the author?
- Is every claimed result `AUDITED`, or an exact external input `QUOTED`, and every packet `TYPESET-AUDITED`?
- Does every public statement earn its place through a distinct reader-facing role and either a real later use or a declared role as a principal conclusion?
- Is every nontrivial step proved visibly or supported by an exact, checked citation, primary where it supports the formulation?
- Can a reader follow the argument forward, with definitions before use and one coherent burden per paragraph or named step?
- Does each major result have distinct motivation, a precise statement, and a useful interpretation without duplicated formulas?
- Does the introduction formulate the problem, state the results, explain the strategy and key ideas, compare the relevant literature exactly, and orient the reader?
- Have the source, bibliography, compilation, every rendered page, and a complete linear reading been checked at the release-candidate revision, with the responsible reviewer recorded?
- Are all remaining limitations stated honestly?

If any answer is no, the paper is not finished.
