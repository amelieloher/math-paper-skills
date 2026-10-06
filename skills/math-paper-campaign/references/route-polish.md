# Route B: polish a checked paper

From a manuscript whose statements and proofs have been mathematically checked to one canonical, publication-ready paper for a declared audience: a reader who knows the field's standard background but not the project's discovery history. Apply the [shared controls](shared-controls.md) throughout. This route does not establish new proofs or formalise anything; a change coming from a formalisation enters only after mathematical review, through the drift protocol.

The route is Phase 0 followed by Phases 1–6. Use the designated style, by default the [house style](../../latex-math-writing/references/house-style.md), to calibrate each phase; it is never a mathematical authority.

## The aim: less reader effort, not fewer lines

Use the shortest form that keeps every load-bearing inference visible. A sentence, display, reminder, or proof step is redundant only when deleting it preserves both correctness and the reader's ability to follow the argument without rebuilding it. Point-of-use hypothesis reminders, the orientation sentence of a long proof, and a non-repetitive interpretation of a principal result are functional exposition, not redundancy.

An editorial pass may reorder accepted material, merge duplicate exposition, inline one-use facts, and replace a reproduced proof of a standard external input by a point-of-use citation, but only when the source contract is `QUOTED`, no later argument uses details of that proof, and the disposition is accepted. Everything listed under [the mathematical contract](shared-controls.md#the-mathematical-contract) stays fixed.

## Readiness

"Checked" is never a free-floating description. Bind it to a commit, hash, dated snapshot, or other immutable revision, and say which statements and proofs the check covers. If the record is incomplete, continue only on packets whose mathematical authority is exact; leave the others blocked and visible (or run [Route A](route-build.md) on them).

Identify the canonical TeX entry point, macro file, bibliography, build command, and source corpus; the principal results, their dependency closure, and all visible gaps or draft markers; the audience, venue, and style; the notation authority and any accepted notation translation; and the external inputs already verified, with their exact locations and adaptations.

Before a full rewrite, obtain the author decisions that can change the paper's spine: target audience, the hierarchy of principal results, canonical notation, consequential merges or demotions of named results, and the deliverable. Do not make these decisions indirectly through prose edits.

## Phase 0: Freeze the brief and baseline

**Input:** the checked manuscript, review records, sources, macros, bibliography, build instructions, audience, and style.

1. Declare the canonical manuscript and the immutable checked baseline, then read the entire current paper, including proofs and consequences.
2. Inventory the theorem surface, definitions, symbols, citations, labels, draft markers, and dependencies.
3. Record the author's voice profile and the selected style authority; when none is designated, use the house style without asking for a new style decision. Select representative opening, statement, proof, and transition pages for later comparison.
4. Record unresolved decisions and any material the check did not cover.
5. Compile the baseline and keep a readable reference PDF.
6. If the brief sets a page limit, measure the frozen definitions and statements typeset alone before planning the rewrite (see [Route A, step 1](route-build.md#1-brief-and-pre-writing-decisions)).
7. For a teaching or expository text, record two or three questions a cold reader must be able to answer after one reading (for example: why a device is needed only once; why the final object is smooth although an error is not zero). Give them to the exposition critic and to the final cold reader.

Record the distinction between the final theorem's objective and the auxiliary quantities used to reach it, and fill the notation map's entries for easily confused terms. Do not apply an earlier finding to an updated manuscript without reading the affected argument again.

**Gate:** the author has settled every decision that could change the spine. For a full-paper rewrite, the ledger accounts for the whole claimed surface; otherwise only explicitly scoped packets with exact authority may proceed, and the rest stays blocked and visible. No rewrite starts from an unnamed or ambiguously checked draft. Every registered packet has a frozen contract and enters at manuscript status `INTEGRATED`.

## Phase 1: Inventory and reduce the mathematical route

Map every public statement and proof route to a reader-facing function. Audit definitions, symbols, displays, and citations for use, duplication, and provenance. Assign a disposition before moving or deleting material. Work backwards from the principal conclusions and forward through the eventual reading order.

### What to remove or merge

- duplicate statements or parallel proofs with no distinct use;
- component extractions, immediate specialisations, and formalisation or API lemmas that can become prose or a point-of-use observation;
- definitions or notation without sustained use: a name must save reader effort or expose structure, not merely save characters (see [artisan-writing](../../latex-math-writing/references/artisan-writing.md#control-notation-and-definitions));
- proof milestones that merely restate the preceding calculation;
- repeated calculations that can be proved once at the right level and cited;
- obsolete labels, only when their enclosing material is explicitly removed, all internal and external references have been checked, and removal is in scope;
- unused section scaffolding, after checking all affected material and recording the disposition;
- discovery-order detours and project-management language that no longer serve the final proof.

Proposed removal of any hypothesis or conclusion is drift. A named result may be merged, demoted, or removed editorially only when each of its accepted claims remains available verbatim at its point of use; otherwise the change also follows the drift protocol.

### What compression must preserve

- every nontrivial inferential edge not supplied by an exact source;
- natural endpoint, sign, normalisation, boundary, measurability, and constant-dependence checks;
- point-of-use reasons that a quoted theorem applies;
- functional repetition that reorients the reader after a long interruption;
- honest uncertainty, draft markers, and limitations.

For a multi-part proposition, count mathematical conclusions, not just numbered items. Organising the statement by use can move subsidiary estimates into labelled conclusions inside the proof without discarding them. Record every old estimate's destination and check every later use, including hypotheses, exponents, normalisation, and constant dependence.

Do not polish prose yet. This phase shortens the mathematical route and removes unused public surface; it does not add intuition or smooth transitions.

**Gate:** an independent mathematical reviewer confirms that each reduced packet has the same frozen contract, complete dependencies, and all later uses accounted for (or a declared role as a principal conclusion). Every merge, demotion, move, or removal has an accepted ledger entry. Mark accepted packets `REDUCED`.

## Phase 2: Replace standard inputs by exact citations

Classify each nontrivial step as proved in the paper; quoted exactly from the literature; an elementary consequence whose complete argument is visible; or heuristic or open and explicitly labelled.

Record every proposed external input in the [citation map](control-artifacts.md#citation-map). Read an authoritative source containing the exact result; prefer the primary source when it supports the present formulation. If a monograph or later definitive source is used, record that and make no priority claim. A bibliography entry, abstract, search snippet, indirect citation, or memory of a standard theorem is not verification. Cite the result at its point of use and say why its hypotheses match. Never invent a source location. If no exact source supports a step, prove it cleanly or mark the claim open; do not hide it behind "standard," "well known," "clear," or "similarly."

Do not cite an earlier private draft in place of a missing argument. If it contains a needed calculation, verify it and integrate the shortest complete version near its use. A substantial auxiliary proof may deserve an appendix, but length alone is not the criterion: the main argument must stay readable and complete. A newly found gap returns to mathematical review before dependent claims are polished as settled. Explain adaptations of a published proof rather than presenting them as a direct application. Use bibliography citations, not floating file nicknames.

Citation checking may run in parallel with Phase 1, but a route may not be compressed to a citation until its status is `QUOTED`.

**Gate:** every external load-bearing step has an exact, checked citation record; every literature comparison identifies a mathematically inspectable difference. Any comparison added later must pass this check too.

## Phase 3: Linearise the argument

Build the paper in dependency order rather than discovery order, so the reader can move forward without repeatedly reconstructing why an object was introduced.

1. Give each section one mathematical objective, accepted inputs, and an exit result, with a short, concrete title naming that objective; keep any qualifier needed to tell it apart from neighbouring arguments.
2. Define an object immediately before its first sustained use.
3. Place a lemma immediately before its first important consumer when the dependency graph allows.
4. Keep one active narrative thread; move auxiliary material away only when the main line stays visible without it.
5. Avoid unnecessary forward references in the detailed argument. A proof outline may preview named results, and an auxiliary proof may be deferred to an appendix or companion under [the deferred-proof checks](../../latex-math-writing/references/artisan-writing.md#deferred-proofs-and-technical-modules): state the needed result with its hypotheses and matching notation, explain its role, give the exact proof location, and keep the dependency noncircular.
6. Give every public result a one-sentence purpose and either a real later use or a declared role as a principal conclusion.
7. Make transitions express mathematical dependence, contrast, or consequence, never merely announce that the paper moves on.

Check the architecture through the distinctions it must preserve: preparation versus conclusion, proving smallness versus transporting it, a local step versus the global count, an estimate in expectation versus one on a common event. These are diagnostic questions, not mandatory sections. Section titles should identify distinct jobs, and a short final assembly proof shows that not every result needs a new layer of machinery.

Write only the connective prose needed to test the architecture; full polish belongs to Phase 4. Before broad drafting, test the explanation on a representative continuous passage with difficult changes of representation, using [the comprehension test](../../latex-math-writing/references/artisan-writing.md#test-comprehension-from-the-readers-text), and repair the presentation before expanding it through the manuscript.

**Gate:** a fresh reader can traverse the dependency chain in one direction; objects precede use; each public result has a later use or is a declared principal conclusion; no two statements do the same job. The author approves the section architecture and any change in the prominence of a named result. Mark accepted packets `ARCHITECTED`.

## Phase 4: Write the argument artisanally

Rewrite each accepted packet in the author's voice, following [artisan-writing](../../latex-math-writing/references/artisan-writing.md) and the selected style. Explain the obstruction before its correction and the consequence after a decisive display; trace remaining errors and preserved properties through a long construction.

### Openings explain at different levels

Use [Ideas before technicalities](../../latex-math-writing/references/artisan-writing.md#ideas-before-technicalities) for section entrances and proof overviews: orient the reader around the task, obstacle, mechanism, and useful output before the full notation. With several alternatives, explain what each achieves and why the procedure can continue; keep exact case conditions for the statement unless the overview would otherwise mislead. Do not imply that every step improves an error when some merely preserve a bound or incur a controlled cost.

Begin a major section with one or two sentences saying what it proves and why, then develop the intuitive mechanism. If a subsection begins directly with a proof, its first paragraphs can introduce the local mechanism; a second pre-proof introduction would only duplicate them. At subsection entrances, apply [Section and subsection openings](../../latex-math-writing/references/artisan-writing.md#section-and-subsection-openings): interlace the local idea with the actual objects, comparisons, and selected formulas needed next. Explain an estimate's mechanism before using its name as shorthand, and identify the error terms under discussion.

Review the openings in two passes. First read them without following references: can a reader explain why the construction helps and, at subsection level, identify the objects and the role of each comparison or error term? Then compare them with the exact statements and proofs: are the essential qualifications still visible, and does every deferred technical detail remain explicit in its proper place? A smoother overview is not permission to remove information or replace a proof by intuition. Avoid a fixed paragraph length or a repeated overview at every boundary.

Apply [Short titles and paragraph headings](../../latex-math-writing/references/artisan-writing.md#short-titles-and-paragraph-headings): separate distinct explanatory parts with short bold `\paragraph{Title.}` headings where navigation benefits; let connected paragraphs share a heading and leave brief openings untitled; keep italic proof-step labels separate. The heading names the idea; the prose must still explain why it works.

### Uniform cognitive burden

Apply [Keep objects recognisable through the argument](../../latex-math-writing/references/artisan-writing.md#keep-objects-recognisable-through-the-argument) at coordinate, basis, normalisation, and approximation changes: the reader must understand how the current unknowns represent the original object and why the new representation helps. Interlace definitions with their uses and explain the role of auxiliary quantities. Measure the meanings and conversions the reader must hold in memory; remove redundant representations and setup to make room for necessary explanation.

Do not force equal word counts or numbers of displays. Each paragraph or named proof step carries one coherent burden: one reduction, one construction, one application of an input with its hypotheses checked, one decisive estimate or calculation, or one consequence that closes the current subgoal. Split a step that needs two independent ideas; merge fragments with no independent inference. A long proof opens with a short route map; a named step's first sentence says what it establishes and why it is needed.

### Explain without bloating

For each principal theorem and other major statement, supply only the explanations that do distinct jobs:

1. **Before:** why the result is needed and what obstruction it resolves.
2. **Statement:** the precise contract, with no motivation or provenance inside the environment.
3. **After:** what the result says in plain mathematical terms, the mechanism when useful, and which later argument uses it or why it is a principal conclusion.

Do not paraphrase a display merely to repeat it. Label heuristic intuition as heuristic. Prefer simple verbs and exact mathematical nouns; remove fancy synonyms, praise, slogans, development nicknames, "hocus pocus" transitions, and generic claims of novelty. Let the mechanism show the strength of the argument. At the point of use, expose every load-bearing inference, hypothesis, and constant dependency; stop when the subgoal is proved. Apply the deletion test only after the logic is visible: if removing a sentence makes the reader reconstruct an essential step or the role of a major statement, keep it.

Use these checks where the mathematics calls for them (they are expanded in [the house style](../../latex-math-writing/references/house-style.md#distinctions-that-make-the-explanation-work)):

- Can the reader name what is averaged or compared and why the operation improves the estimate? Do not argue that fluctuations are controlled because contraction succeeds if fluctuation control is what proves contraction.
- Does a failed test permit growth, and what pays for it? Explain the growth bound and the compensating quantity, including overlaps and changes of normalisation. Telescoping does not remove every cost automatically.
- When a construction restarts, where does its small input come from, and which earlier information survives? A new name or initialisation index is not a source of smallness.
- Are the mathematical referents exact? Use identifying indices and arguments, not undeclared shorthand; distinguish related measurements and explain why both are needed, what converts one into the other, and which estimate needs that form. For a combined progress count, identify each component, its reference state, and the steps that change it; do not confuse a retained initial value with the current one.
- Is an argument named for what it accomplishes, or only for a routine tool? Explain the actual comparison and the role of its errors, and keep the tool's precise use in the proof. Remove empty transitions and duplicated roadmaps, not the orientation or unique information they may contain.
- Does each long estimate have an interpretation of its terms and a stated use? Keep essential constant dependencies at the choices and in the statements, not in repeated lists in section introductions.
- Is a claimed uniformity actually explained: one event, radius, or family chosen before later parameters rather than separately for each?

Use the representative passage tested in Phase 3 to calibrate voice, granularity, and level of explanation before applying the style throughout. When the author has already designated a style, continue under it without a new confirmation; ask only when a consequential stylistic choice is unresolved.

**Gate for each packet:** a reviewer other than the editor performs a mathematical-preservation review, which classifies every new explanatory sentence and table entry as true or false (see [shared controls](shared-controls.md#reviewers)), and a separate exposition review. After the accepted exposition repairs, mark the packet `EXPO-AUDITED`. Then compile the smallest target and inspect the affected and neighbouring pages; mark it `TYPESET-AUDITED` only after those rendered pages are accepted.

## Phase 5: Write the final introduction

Write the final introduction only after the theorem surface, body architecture, notation, and citation map are stable, following [the introduction guidance](../../latex-math-writing/references/artisan-writing.md#build-the-introduction-after-the-body-stabilises). Its reader-facing roles:

1. **Problem formulation.** Begin from the object, equation, or phenomenon; state the regime and the question precisely enough to motivate the result.
2. **Main results.** Give an informal result with the inspectable rate, exponent, scale, or distinction before the formal theorem; then state the principal results economically.
3. **Strategy and key ideas.** Explain the true obstruction, the decisive new mechanism, and the object tracked through the proof. Do not substitute a list of section titles.
4. **Comparison with previous literature, when relevant.** State the exact prior conclusion and the exact improvement, removed assumption, new regime, or new uniformity, with verified citations.
5. **Outline of the paper.** Only the roadmap that helps the reader navigate the proof.

These roles impose no fixed order or length. Under the house style, put the concrete contribution and principal theorem early, then develop context and mechanism; a substantial conceptual account and proof outline may occupy their own sections when that lowers the reader's burden, and their prose must explain the proof rather than list section names.

Apply the ideas-first test to the abstract and proof outline: keep the result's substantive rate, regime, and consequence; omit secondary formula descriptions with no intelligible role there; explain how the argument earns its conclusion before giving navigation references; do not export the body's inventory of auxiliary parameters into the introduction.

In motivating examples, describe what changes physically or probabilistically as a parameter varies before naming a transition or scaling regime; make thresholds intelligible through the model, keep the scope of the cited literature, and connect the example to the theorem's quantitative question. In the strategy, identify the objects in every comparison rather than naming a routine tool. Introduce technical terms through the object they describe, cross-reference an assumption when invoking its parameter, and explain the role of a condition rather than crediting an undefined exponent. When comparing proof costs with earlier work, distinguish how often a step is repeated from the scale separation it requires, and verify the claimed saving against both proofs. If a formalisation is discussed, disclose its actual coverage and any differences in contract rather than claiming that a build certifies the printed theorem.

Every promise in the introduction must point to an accepted body result or section. Keep heuristic predictions visibly distinct from proved claims. Write or revise the title and abstract now when they are part of the deliverable.

**Gate:** every theorem claim, contribution claim, and promise maps to an `AUDITED` or `QUOTED` body node; every external factual or result attribution has an accepted citation record; heuristic claims are labelled and sourced when attributable; grouped landscape citations are checked bibliographically and for relevance. The author approves the contribution hierarchy, novelty language, and positioning in the literature. A fresh exposition reader reviews the introduction; compile and inspect its rendered pages. Record this as a manuscript-level introduction gate in the ledger, not as a statement-packet status.

## Phase 6: Publication audit

Run the [final audit](shared-controls.md#final-audit) at a named revision, with these additions:

- compare the opening page and representative dense body pages with the selected style's explanatory and visual acceptance checks, not just the preamble or font names; venue formatting may change the visual match, but the explanatory standard stays, and the constraint is recorded;
- read the contents titles together for brevity, precision, and distinct roles, and inspect bold paragraph headings for consistent style, useful grouping, and sound page breaks;
- in the linear-reader review, require a reconstruction from the reader-facing text and exact locations where the reviewer supplied missing explanations; section-by-section success does not establish continuity across boundaries; for companion modules, also test reading from their declared prerequisites alone;
- as a supplementary orientation test, read all section openings in order, then the subsection openings with their next statements: the first pass should explain the strategy, the second should identify the local quantities and comparisons without sending the reader backwards; check that references such as "that matrix" or "the second quantity" have clear antecedents and that repeated roadmaps serve a distinct local purpose;
- check terminology globally, including headings and statements, without blindly replacing mathematically different uses; regress preserved intermediate estimates as well as theorem surfaces; inspect fractions in context, proof-step styling, and link destinations, not merely the presence of preferred commands in the source.

The manuscript is publication-ready only when it passes the [completion test](shared-controls.md#completion-test). "Compiles" is necessary but not sufficient.
