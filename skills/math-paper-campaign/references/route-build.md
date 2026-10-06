# Route A: build the paper

From a proof outline, notes, a formal development, or an earlier draft to a complete paper whose every claim is reviewed. Apply the [shared controls](shared-controls.md) throughout.

## 1. Brief and pre-writing decisions

Write the brief described in [control artefacts](control-artifacts.md#paper-brief). For a complete rewrite, read the entire current manuscript before prescribing its architecture, and judge comparable passages, including dense proofs and final consequences, against the [house style's explanation levels](../../latex-math-writing/references/house-style.md#calibrate-the-level-of-explanation) or the designated style. Confirm the current revision and preserve concurrent edits; do not revive diagnoses of text that has since changed without checking it.

For a paper started from scratch, do not create the canonical manuscript until the author has settled every decision that could change the paper's spine: model assumptions and normalisations, geometry or regime boundaries, the hierarchy of principal results, notation and source authorities, authorship metadata, and delivery format. Keep a short list of open decisions and obtain explicit approval for consequential theorem surfaces. A decision may be deferred only when it cannot affect the first writing route; record that boundary. For a rewrite, this gate applies before opening a new canonical manuscript, not before inspecting the old source.

When the brief combines a page limit with a completeness requirement (every definition in the document), typeset the frozen definitions and statements alone, in dependency order, and measure them before allocating section budgets. Budgets summed from estimates are targets, not measurements; never tell the author that a length is or is not achievable without a compiled measurement. If the measured surface plus minimal prose exceeds the limit, present measured options to the author: for example a short argument with a reference part in the same PDF (see [two routes and short forms](../../latex-math-writing/references/artisan-writing.md#deferred-proofs-and-technical-modules)), a change of scope, or a longer continuous text.

## 2. Freeze the mathematical spine

Build a dependency graph from the principal conclusions backwards to accepted inputs. For each proposed public statement, record a specification envelope in the ledger: its role and later use, permitted hypotheses, required conclusion and normalisation, constant dependencies and uniformities, and direct dependencies with the exact source or proof route.

Reject a public result that is merely a component extraction, an immediate specialisation, a proof-local identity, or a formalisation convenience.

When the paper digests a long source, establish the spine independently at least twice (for example by the orchestrator and by an independent reviewer) before freezing it. For statements that describe one jointly chosen object, record the joint quantifier structure and the acyclic order of construction in the ledger.

Freeze the principal theorem statements before building their routes. Obtain explicit approval when a theorem choice is ambiguous or consequential. Local lemma wording may be frozen just before its proof is drafted, but its envelope must already be stable.

## 3. Reverse viability audit

Before drafting a theorem's route, audit it backwards from the exact conclusion. Verify that:

1. every load-bearing edge has an accepted proof or an exact external source;
2. quantifiers, spaces, constants, normalisations, boundary conditions, and measurability agree across edges;
3. no input is circular or shaped like the desired conclusion;
4. adaptations from another geometry, regime, or notation track every distortion;
5. the least certain edge has received an adversarial check.

If a genuine research gap remains, record it and pause the manuscript claims that depend on it. A plausible strategy, a formal wrapper, or a review report is not a proved theorem.

### Diagnostic detours

Attach any proof investigation the audit exposes to one active ledger row: the parent statement, the exact question, the affected edge or hypothesis, and its possible effect on the contract. Work in a bounded scratch note, never in the canonical manuscript, and end with exactly one disposition:

- `USED`: integrate the accepted argument into the parent proof;
- `REVISE`: reopen the parent contract or a dependency;
- `REJECTED`: discard the route;
- `OPEN`: leave the parent honestly blocked.

Update the ledger and dependency graph before resuming manuscript work. A diagnostic note must not become a parallel manuscript or spawn unrelated successor work.

## 4. Pilot the explanation

For a substantial new exposition or rewrite, test the approach before broad technical expansion. Draft a brief provisional explanation of the construction and one representative continuous passage containing difficult changes of representation. Apply [the comprehension test](../../latex-math-writing/references/artisan-writing.md#test-comprehension-from-the-readers-text) to the reader's text, and repair a failed explanation before commissioning more writing that depends on it. Measure the pilot's length as well as its readability. The pilot tests the accepted mathematical route; it does not replace the statement lifecycle or finalise the introduction early. Keep the previously reviewed drafts (for example in a `v1/` folder) so that a rewrite can be checked line by line against them.

## 5. The statement lifecycle

Take each public result through these steps, one packet at a time.

**Nominate.** Record its role, dependencies, source or proof idea, later uses, and the environment rank it justifies (theorem, proposition, lemma). Remove it if the calculation belongs inside another proof.

**Workshop the statement.** Check mathematical shape, minimality, endpoints, fit with the proof, uniformities, and clarity for the reader. Freeze the exact contract once accepted.

**Draft the proof.** Write against the frozen contract. Start with the decisive move, introduce only useful local notation, and expose every load-bearing inference. If the proof needs a changed contract, stop and reopen the workshop.

**Review the mathematics.** Use an independent reviewer as described in [shared controls](shared-controls.md#reviewers). Request exact objections or a small repair, not a replacement manuscript. After any later exposition rewrite of the packet, review its new explanatory sentences and table entries again.

**Review the exposition.** Read the statement alone, then the first sentence of each proof paragraph. Apply the deletion, duplication, notation-cost, internal-language, and source-fidelity tests. Then check that:

- the obstruction motivates the construction, and decisive displays have explained consequences;
- the reader can track remaining errors and preserved properties, and useful reminders and complete theorem conditions are kept;
- the reader can distinguish the final goal from preparatory estimates, identify the source of smallness, and explain any growth or failed step;
- related quantities have distinct meanings, symbols keep their identifying arguments, and the prose names an operation before using its estimate as shorthand;
- the reader can track the original objects through the current unknowns and reconstruct the next inference (the comprehension test). Record explanations the reviewer supplied from its own knowledge as findings, even when every symbol is defined. Keep this first reading separate from the later source comparison.

These tests expose unclear reasoning better than a request to make a paragraph shorter. Compare representative rendered pages, including dense proof pages, with the selected style's visual profile. Editorial changes must not silently alter the frozen contract.

**Integrate.** The canonical editor rewrites the accepted content into the paper's voice and edits the TeX. Mark the packet `INTEGRATED`, and `EXPO-AUDITED` once the exposition review's accepted repairs are in the manuscript.

**Verify and checkpoint.** As in [shared controls](shared-controls.md#checkpoints): compile, run checks, and inspect the affected and neighbouring pages; mark the packet `TYPESET-AUDITED` once those pages are accepted, and update the ledger.

## 6. Section and subsection gates

Before a major section, write a short charter: objective, accepted inputs, included material, excluded material, least certain edge, and exit test.

At a subsection boundary, read linearly and check that notation is introduced once, connective prose motivates the next result, no two statements duplicate each other, every public result has a later use, and the ledger matches the TeX. Also check:

- the [level of the openings](../../latex-math-writing/references/artisan-writing.md#section-and-subsection-openings): a section gives the intuitive strategy; a subsection connects it to the objects and estimates used next;
- [titles and paragraph headings](../../latex-math-writing/references/artisan-writing.md#short-titles-and-paragraph-headings): short and concrete, with bold `\paragraph{Title.}` headings for distinct explanatory parts and the separate italic proof-step convention;
- for a narrative with a technical companion, [the deferred-proof and module checks](../../latex-math-writing/references/artisan-writing.md#deferred-proofs-and-technical-modules): usable statements and exact proof addresses stay synchronised, modules read from their declared inputs, and authorised notation conversions agree across both documents, figures, and captions (a matching letter does not establish a matching quantity).

Before drafting companion parts in parallel, fix each part's export interface: the labelled statements it provides. After drafting, run a reconciliation pass that discharges every assumed input by citation. A fact proved inside a proof may be cited only once it has become a clause of a statement. The final assembly is a real review, not a formality: re-derive the relations it combines.

At a section boundary, obtain fresh mathematical and exposition reviews. Do not start the next major analytic section while a load-bearing result in the current one is merely drafted or self-certified.

## 7. Rewrite an existing manuscript

When rewriting rather than drafting from scratch:

1. inventory the old theorem surface, definitions, dependencies, citations, and unresolved gaps;
2. give each old result a disposition (`RETAIN`, `REWRITE`, `MERGE`, `DEMOTE TO PROSE`, `MOVE`, `REMOVE`);
3. freeze the new paper's spine independently of the old section order;
4. reuse mathematics only after checking it against the new assumptions and notation;
5. rewrite one accepted statement and proof at a time.

An older paper may supply a proof route without supplying the final exposition. When a large proposition is reorganised around fewer useful conclusions, keep its needed subsidiary estimates as labelled conclusions inside the proof and map every old use to its new location. When a private draft supplies a missing justification, integrate the shortest complete argument near its use after review; do not cite the draft or grow an appendix to preserve the discovery record. An actual gap reopens the mathematical route, not just the prose.

## 8. Finish

Once every claimed result is `AUDITED` or `QUOTED` and the theorem closure is stable, decide whether the body still needs restructuring, and do so before writing the introduction:

- **If it does** (duplicated routes, discovery-order structure, uneven exposition), continue into [Route B](route-polish.md) from its Readiness section and Phase 0, taking the current revision as the checked baseline. Route B writes the introduction in Phase 5 and ends with the Phase 6 audit.
- **If it does not,** write or fully revise the introduction following [Route B, Phase 5](route-polish.md#phase-5-write-the-final-introduction), including its gate, then run [Route B, Phase 6](route-polish.md#phase-6-publication-audit): the shared final audit plus its style, title, and orientation checks, and the completion test.

Call the paper complete only when every claimed result is accepted, every external input is sourced exactly, every page has been read in rendered form, and every remaining limitation is stated honestly.
