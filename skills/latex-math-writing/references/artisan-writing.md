# Artisan Mathematical Writing

The detailed writing guidance behind the `latex-math-writing` skill.

Write for a mathematically sophisticated reader who knows the field but not the project's development history. Produce finished mathematical prose, not a transcription of notes, formal code, agent reports, or project-management vocabulary.

## Establish the local authority

Before drafting, inspect the canonical manuscript, macro file, bibliography, nearby papers named by the author, and any notation or style guide. Follow the priority order in [writing-rules.md](writing-rules.md). For whole-paper writing and polishing with no other designated style, read [house-style.md](house-style.md): it supplies the default exposition and visual target and a starting preamble.

Preserve established symbols and macro spelling. Record and resolve genuine conflicts before writing. Do not silently change a mathematical object's meaning to match a convenient notation.

When the author designates a notation source for a rewrite, compare meanings, arguments, units, normalisations, and conventions before adopting its symbols. Extend it conservatively for objects it does not name. Keep any correspondence in the existing internal notation map; the reader should learn one presentation. Mathematical source fidelity preserves claims and proof obligations without requiring unreadable source notation to be copied. Apply an authorised notation conversion consistently to equations, statements, proofs, figures, and captions, checking its mathematical consequences.

## Craft statements

- Put only the mathematical contract in a result environment. Keep motivation, provenance, interpretation, and proof strategy in surrounding prose.
- Order hypotheses naturally and quantify every parameter. State spaces, boundary conditions, normalisations, probability assumptions, and constant dependence at the level needed to understand the conclusion.
- Flag unused hypotheses and conclusions without a reader-facing role; changing them requires the mathematical-contract review, not a prose edit. Preserve every essential support, uniformity, regularity, and parameter-dependence clause even in a long statement.
- State what the proof actually establishes. Do not add generality merely because it looks inexpensive.
- Use `theorem` for principal results, `proposition` for memorable load-bearing results, and `lemma` for independently useful support. Keep one-use calculations and immediate specialisations inside proofs or prose.
- Prefer one coherent statement over several component projections with identical proofs.
- Organise a multi-part proposition by what the reader will use, not by the order of its derivation. Keep subsidiary estimates as labelled intermediate conclusions in the proof when they remain needed. Before regrouping, account for every old conclusion and its later uses; fewer statement items must not mean fewer available estimates.
- Express genuinely different input regimes as explicit alternatives. For an iterative step, make the cases disjoint and exhaustive, and show that the output meets the next step's input conditions. Do not leave the reader to reconstruct a regime from several implication-shaped hypotheses.
- Make introductory theorems self-contained enough that a reader can tell what is asserted without following a chain of forward references.
- When several statements describe one jointly chosen object (parameters, a core, a background profile), write one explicit binder at the head of the first ("Statements X to Z assert one joint choice ...") and give the quantifier structure and the order of construction. Without it, their mutual references read as a cycle.
- Cite statements by label, never by a typed number, and settle numbering only after each statement's home is fixed.

Read a statement once without its proof. If its role, objects, or uniformities are unclear, revise it before drafting the proof.

## Write proofs artisanally

- Begin with the decisive mathematical move: choose the minimiser, write the equation, introduce the decomposition, condition on the sigma-field, or invoke the exact input.
- Let paragraphs expose the logical phases and displays carry calculations. Give each paragraph one mathematical purpose.
- Make the first sentence of a proof paragraph reveal what that paragraph accomplishes.
- Cite an accepted result at the point of use. Verify that its hypotheses, normalisation, quantifiers, and conclusion match the present use.
- Introduce proof-local notation only when it pays for itself through repeated use or exposes structure.
- Do not hide a load-bearing step behind “standard,” “straightforward,” “clearly,” or “similarly.” Supply the argument or a precise citation.
- Check endpoint cases, signs, operator order, transposes, boundary terms, measurability, independence, scale thresholds, and constant dependence wherever relevant.
- After a long estimate, identify its terms by origin and explain the next use: for example, interior averages, boundary pieces, and earlier scales. A list of term names without the comparison producing them is not an explanation.
- Choose constants in dependency order where uniformity matters. State essential dependencies in the theorem and at the choice, not repeatedly in intuitive overviews. Explain which decay absorbs which growth; do not replace that reason by “take the constant large.”
- Preserve the claimed order of construction: one event, radius, approximation, or family chosen before later data is stronger than one chosen separately for each datum. Explain the common choice at the point where the proof earns it, rather than hiding it in “uniformly.”
- Stop when the assertion is proved. Do not end by restating the theorem.

If the natural proof requires a stronger hypothesis or produces a weaker conclusion, stop and reopen the statement. Do not repair statement drift silently in prose.

## Control notation and definitions

- Treat every new symbol as a cost to the reader. Avoid aliases used once or twice, especially names for explicit expressions. Repeated use alone does not justify a name that makes the underlying object harder to recognise.
- Introduce structural notation immediately before its first sustained use; keep temporary notation inside the proof that needs it. Alternate definitions with their explained uses instead of depositing a large alphabet before its first application.
- Introduce an object's mathematical kind and job: a component, integral, error function, basis vector, or parameter. Say what the next equation or estimate needs it for.
- Define a standard object once. Recall it later when needed, especially after a long interruption or at a boundary where related averages, normalisations, or indices could be confused. A symbol guide can help a long paper but cannot replace point-of-use explanation.
- Prefer the canonical normalisation already present in the problem, such as an average rather than an arbitrary unnamed constant, when this clarifies the statement.
- Preserve project macros instead of expanding them into raw notation.
- Remove vacuous factors and decorations.
- Distinguish genuinely different objects explicitly; never reuse a familiar symbol for a nearby but inequivalent quantity.
- Close every definition: each operator and symbol in a public statement has a defining display inside the document, not only in a macro comment, a notation inventory, or a companion.
- State a normalisation at the definition, including what is absent. For a symmetric bilinear form: "no factor $\frac12$ in $B$; the quadratic term is $\frac12 B(w,w)$." Call a quantity that varies a coefficient, not a constant.
- A summary of a definition or lemma (a reading key, a table of rules) is an explicit selection of its consequences, never a second definition. Keep each row's domain ("for $f$ in class $X$") and check the summary as a statement.
- Use the actual mathematical expression when referring to an object, including the indices and arguments that identify it. An undefined shorthand such as `$\mathcal P+D$` does not identify the grid, scale, or initialisation. A declared, repeatedly useful proof-local abbreviation is different; do not introduce it just to shorten an opening.
- When two quantities measure related effects, say what each compares, what normalisation it uses, which is fixed or evolves, and why both are needed. An additive increment, a cumulative difference, and a weighted history are not interchangeable just because one bounds another. Explain the conversion and its use: for example, separating old and new increments permits an update estimate, while summing intervening increments gives differences over a longer interval that a different comparison can estimate. Naming summation by parts alone does not explain why it helps. A simple limiting example can make the distinction memorable.
- Name a quantity for its mathematical meaning, not the construction's nickname. Distinguish distortion of coordinates or a grid from properties of a coefficient or reference bound; do not claim coordinate invariance without checking it. Once terminology is settled, check all reader-facing occurrences, while preserving genuinely different technical uses.

### Keep objects recognisable through the argument

Having defined every symbol does not establish that a reader can follow the mathematics. At each substantial transformation, keep the original object and the purpose of its new representation visible.

- Prefer recognisable component, derivative, or increment notation when separate aliases would conceal their common origin. Retain useful names for distinct objects or repeated expressions when they reduce reader effort or expose structure; this is not a ban on auxiliary notation.
- Choose the representation actually used in the equations and estimates as the main unknown when the task permits it. If only a normalised quantity is used, define it directly and explain how it reconstructs the original field. Do not route every use through an otherwise dispensable intermediate unknown.
- Distinguish independent variables, fixed parameters, evolving unknowns, and arguments supplied by a coordinate map. A physical field and its profile can have different arguments. State what is held fixed in derivatives; suppress arguments only after establishing the convention.
- Before using equations in new coordinates or a new basis, explain the conversion, its purpose, and how to return to the original object. For amplitude equations, identify the perturbation, its constraint, the basis, and the meaning of its coefficients before presenting their ODE. Make unit versus nonunit basis conventions and their scaling factors explicit.
- Keep exact fields, leading approximations, complete perturbations, and corrections distinguishable. An increment of an average is not the average itself. Explain which average or normalisation is used and recall the distinction where a later transition could obscure it.
- Explain what auxiliary quantities determine or preserve, beyond their definitions. If restoring cumulative integrals restores a downstream field or constraint, identify that dependence locally and cite its verification. The reader should understand why the integrals are targets without looking up their technical proof.

For example, introducing `$a=\partial_1u$`, `$b=\partial_2u$`, and then `$c=a+\lambda b$` can obscure a statement about the directional derivative of `$u$`. Write that derivative directly when the aliases have no separate role, or explain the directional-derivative interpretation before using `$c$`. Shorter formulas are not necessarily easier to read.

Assess the simultaneous meanings and conversion relationships the reader must remember, not merely the number of symbols or pages. Make room for explanatory bridges by removing redundant representations, repeated setup, and duplicated calculations. Moving frequently needed definitions to a glossary or appendix can shorten the main text while increasing reader effort.

## Write reader-facing prose

- Replace internal names such as “gate,” “certificate,” “consumer,” “interface,” or development nicknames by mathematical language unless the term is standard or explicitly motivated.
- Use connective prose to explain why the next definition or result is needed. Do not summarise the previous display in different words. A sentence saying that objects “provide the data used below” should identify the actual assumption or estimate they enter, or be deleted if it adds no information. Prefer an explicit relation such as “the support lies inside the domain” to an unexplained nominal condition such as “containment.”
- Avoid announcing a paragraph's plan when its opening mathematical sentence can perform the transition directly.
- Use active voice when it identifies the mathematical action; use passive voice when the actor is irrelevant.
- Do not praise an argument. Show its mechanism.
- Apply the deletion test to every sentence, display, label, title, hypothesis, and conclusion: remove it if no mathematical or expository function fails.
- A heuristic or motivating sentence is a mathematical assertion with a scope. State the scope (values or all derivatives; which region; generic or special data; which row or term), or say only what is true. Preserving every formula in a rewrite does not make the new explanatory sentences true: they need the same mathematical check.
- Stop compressing when another deletion would hide logic or make the reader reconstruct a load-bearing step.

### Ideas before technicalities

An abstract, proof outline, or section opening should give the reader a reason to follow the mathematics before asking them to remember its machinery. Read the relevant statements and proof first, then explain the causal structure: what has been achieved, what still prevents the next step, how the proposed construction overcomes that difficulty, and what it supplies afterwards. These are questions to answer where useful, not a compulsory four-sentence template.

- Introduce a tracked quantity through its job: which error it measures, why that error matters, and why simpler information would not suffice. Defer tuples of inputs, auxiliary indices, exact thresholds, and exhaustive case lists to the definitions and statements unless they are needed to understand the idea. Keep the principal result's meaningful rate or scale visible.
- Explain a mechanism, not just the name of its estimate. Say what is averaged, compared, partitioned, or controlled, and why that operation helps. In an iterative argument, distinguish a step that improves a bound from one that merely carries it forward. Explain where initial smallness comes from; neither restarting a construction nor renaming an error creates it.
- Name an argument by its substantive operation or conclusion, not merely a routine tool it uses. “Cutoff argument” rarely explains a proof strategy: identify the functions or energies being compared and the error being controlled. In the technical proof, still introduce the cutoff and explain its actual purpose, such as permitting integration by parts without boundary terms. Do not replace the phrase mechanically by another generic name or ban legitimate technical uses of the tool.
- When a step can fail, say what fails and what information the failure supplies. If repeated failures are limited by a decreasing quantity, explain that accounting. Do not describe conditional contraction as unconditional improvement or omit an additive error because its formula is deferred.
- Use mathematical nouns with identifiable referents. A term such as “response,” “stability,” or “transport” needs an object and a meaning at first use; it is not a substitute for explaining the energy, solution, estimate, or geometry involved. A transition should identify the next mathematical need, not merely announce “the remaining definitions.” Established terminology remains useful once explained; this is not a word blacklist.
- Separate an auxiliary estimate from the final conclusion. Explain what small fluctuations, slow variation, or a favourable geometry still leave unproved, and identify the additional argument. Never reason “we control the fluctuations because we contract” when their control is an input to contraction.
- Explain the price of an unsuccessful step as well as its compensating information. If errors may grow, state how growth is controlled and later recovered. A telescoping quantity does not make the step free: account for overlaps, changes of normalisation, and jumps between constructions where they occur.
- Distinguish related parameters in prose: what each measures, what can change, and what remains fixed. State which data a constant depends on in terms the reader can recognise. Changing coordinates may clarify that dependence without removing it.
- When combining several quantities to count progress, identify each one before discussing its change. Explain why a logarithm or a weight is useful and which kind of step improves which component. Name the matrix, scale, or other reference state defining a comparison; distinguish a retained initialisation value from a current or terminal value. “That matrix,” “the first quantity,” and “the second quantity” work only with immediate, unambiguous antecedents. Check the actual definition in the proof before simplifying its description.
- End with references that help the reader locate the argument, not a second technical summary. A roadmap explains the contribution of each section; it does not merely list section titles. Read neighbouring overviews together and shorten duplicated navigation, retaining local orientation after a long interruption and any unique hypothesis, uniformity, or mechanism that the repeated passage also explains.

For example, when a stability estimate permits a controlled increase in error, “We apply stability and reinitialise” leaves the important point unsaid. An explanatory version is: “Switching approximations may enlarge the error. We first reduce it enough that, after the switch, the next stage still starts within its required tolerance.” Use such an explanation only when the proof actually provides that reserve; do not invent a mechanism to improve the prose.

Some devices help readers, especially in teaching texts: one sentence a reader should remember, placed directly before each major statement; tables for parallel cases, classes, operations, and exponents; words beside symbols at first use ("the defect $D$, the correction $\pi$"); and, in the plan, a short list of distinctions that must stay visible (two different averages of the same field; a leading term and the complete object).

After rewriting, compare the old and new passages for mathematical information, not word overlap. Every omitted technical condition or estimate must remain explicit in the relevant definition, statement, or proof; retain a verbal qualification in the overview when omitting it would mislead. Check especially improvement versus preservation, conditional versus unconditional conclusions, constant dependence, and control of earlier errors. If a detail exists only in the old paragraph, preserve or relocate it within scope. When a simplification could appear to remove content, explain briefly in the handoff what was deferred and where it remains.

### Section and subsection openings

Calibrate the opening to its role in the argument. Under the house style, use this distinction at each section and subsection entrance, with length proportional to the orientation the reader needs; a short transition can suffice. Follow another author's designated conventions when they differ.

- **A section opening gives the intuitive picture.** First orient the reader in one or two sentences: what is proved here and why it is needed. Then explain the obstacle and why the main idea works. Keep the mathematical referents concrete; a familiar formula can clarify them, but defer auxiliary indices and technical conditions unless needed for the mechanism. A section map alone does not explain the argument.
- **A subsection opening connects that picture to the local mathematics.** Interlace intuition with the notation and comparisons used next. Identify what is averaged, compared, decomposed, or estimated, why this operation helps, and which objects or error terms the next statement must control. Use a formula when it identifies an object or relation more clearly than a long verbal description; explain what that formula does. Introduce or recall the needed notation locally, without reproducing the entire statement or proof.

Name an operation before relying on shorthand for it. “The recurrence bounds the new error” helps only if the reader knows which quantities are related and where the gain comes from. “The same losses control the remaining terms” needs identifiable losses and terms: name the relevant quantity and explain the comparison that produces it. Established terminology is useful once its local meaning is clear; it is not banned.

For example, a section may explain that averaging reduces randomness but that a discrepancy from the quantity of interest must also be controlled. Its subsection can identify independent copies of a variable, state that their average has variance equal to the individual variance divided by their number, and explain which estimate bounds the discrepancy. The technical description makes the mechanism precise; it does not replace it. Use only mechanisms and hypotheses actually supplied by the proof.

Conciseness means removing repetition, not targeting a word count or replacing an explanation by a string of symbols and citations. Keep the causal links that let the reader understand why the estimate is plausible, including when it only preserves control or allows growth. Do not repeat the whole section overview at every subsection. On rereading, ask: does the section opening explain why the strategy works, and does the subsection opening let the reader identify the objects, the decisive comparison, and the role of its error terms? Apply the information-preservation check above at both levels.

If a subsection begins directly with a proof, its opening proof paragraphs can perform this orientation; do not add a duplicate pre-proof introduction merely to satisfy the heading hierarchy. For a short assembly argument, choosing the parameters and applying the named inputs may already be the clearest opening.

### Short titles and paragraph headings

Keep paper, section, subsection, and paragraph titles short and crisp. Name the mathematical object, operation, or goal; leave the explanation to the opening prose. A few words often suffice, but do not impose a word limit or delete a qualifier needed to distinguish two different arguments. A title such as “Contraction” is ambiguous when the paper contracts several quantities: identify the relevant object or use a concise description of the section's scope. Avoid process nicknames and titles that read like miniature abstracts. Another author's conventions and mandatory venue formatting retain priority.

Use headings to reveal the grouping of ideas, not to label every paragraph:

- In a long proof outline or section opening, give a distinct explanatory part a short bold run-in heading using `\paragraph{Title.}`, for example `\paragraph{Averaging.}` or `\paragraph{Comparing the means.}`. One heading may govern several connected prose paragraphs. Keep short transitions and continuous explanations untitled; do not impose a fixed number of headings per section.
- Do not imitate an expository heading with `\emph{Title.}` or an ad hoc `\textbf` prefix. Use the document's paragraph command consistently and ensure it renders bold and run-in. Check the class and existing heading configuration first; standard `article` already provides this style. Do not add a package or alter other heading levels merely to obtain it.
- Keep the formatting roles separate. Bold expository headings do not replace ordinary emphasis, theorem-item labels, or numbered proof steps, which keep the italic form `\emph{Step 1: Description.}`. Do not convert every italic phrase into a paragraph heading.
- A heading is a signpost, not the explanation. Preserve the intuitive mechanism in section openings and the intuition interlaced with precise mathematics at subsection openings. Shortening a title must not shorten away the argument beneath it.

Read the titles together in the contents list and inspect the rendered transitions. Check that they identify distinct jobs, that paragraph headings do not interrupt a continuous argument, and that their spacing and page breaks are sound. Preserve labels and references when renaming headings; a scoped title or formatting edit does not authorise rewriting the surrounding mathematics.

### Deferred proofs and technical modules

When a narrative defers proofs to an appendix or companion, give the usable statement locally with its necessary hypotheses and matching notation. Explain its role and identify its exact numbered proof location, checking the reference in the assembled documents. Make clear whether a public result is proved here, proved later, or supplied elsewhere. A reader granting the deferred results should still understand the construction without consulting the companion to discover what the objects mean.

A technical module should state its mathematical problem, declared prerequisites, output, and relevant preserved properties. Shared definitions should precede their consumers or have an explicit accessible prerequisite location. Test modularity by reading from those inputs without reconstructing the preceding proofs; file boundaries and short page counts do not establish independence.

**Two routes and short forms.** Use this only when a page limit, together with a requirement that every definition appear in the document, makes complete statements at first use impossible; otherwise keep complete statements where they are first used. First measure: typeset the definitions and statements alone, in dependency order. Then keep one document with two routes: an argument read in order, and a reference part, ordered by dependency, that holds each complete definition and statement exactly once. At first use in the argument, give a short form: the consequences used, introduced by the exact reference and the inputs. A short form is not a numbered environment and carries no label. It never says "under suitable assumptions", never weakens or strengthens, and shows every hypothesis that a later on-page proof checks. A display copied from the complete statement cites the original instead of carrying a label. Moving definitions out shortens the reading route, not the document: report both lengths.

## Rewrite from another paper or proof source

Treat an earlier manuscript, proof outline, formal proof, or source paper as mathematical evidence, not as automatically acceptable prose.

1. Identify the exact result, hypotheses, notation, and dependencies being transferred.
2. Check every adaptation in geometry, normalisation, boundary conditions, probability assumptions, and constant dependence.
3. Specialise overly general source theorems to the assumptions of the new paper when doing so removes unused parameters and jargon.
4. Rewrite accepted content in the canonical paper's voice. Do not paste raw agent prose, proof-assistant scaffolding, or source formatting into the manuscript.
5. Cite the source exactly where its result enters and distinguish a quoted input from a result proved in the paper.

An earlier private draft is not a substitute for an accessible mathematical argument. When a needed justification exists only there, verify it and integrate the shortest complete version near its use. Use an appendix when separating a substantial auxiliary argument genuinely helps, not to avoid explaining a missing step. Distinguish a proof adaptation from an exact theorem application, and supply the changed argument. Describe published work through its bibliography citation and mathematical content, not a floating file nickname or unexplained abbreviation. Internal filenames and development records belong outside reader-facing prose.

## Build the introduction after the body stabilises

Use the introduction to locate the problem, state the contribution, and orient the reader:

The roles below need not occur in this order. Under the house style, reach the principal result early, then develop the context, conceptual explanation, and substantive proof outline at the length the mathematics needs. Keep that outline distinct from the eventual proof and identify deferred technical results precisely.

1. introduce the classical problem and relevant regime;
2. explain the strongest pertinent prior results and remaining gap with precise citations;
3. state the model and assumptions before the main theorems need them;
4. state the principal results economically;
5. explain the new mathematical mechanisms and proof architecture;
6. give only the roadmap that helps navigation.

Draft provisional theorem statements and a brief explanatory spine early when needed, but write the final introduction after the theorem dependency closure and body are stable. Finalising the introduction late is compatible with testing the continuous explanation early.

For physical or probabilistic motivation, explain a concrete model and what changes when its parameter changes before naming a transition or scaling regime. A limiting case can expose the mechanism: which paths, interactions, or motions become possible or impossible? Explain any threshold in terms of that model, then connect it to the paper's quantitative question. Retain citation scope and distinguish earlier predictions or simulations from the theorem proved here; clearer wording must not introduce a stronger scientific claim.

In the abstract, say what is proved, under which meaningful assumptions, with what rate or dependence, and why the principal consequences matter. Do not inventory the terms of a technical tail bound without explaining their meaning. In a proof outline, identify assumptions by their established labels when a parameter first matters; a condition such as `$\gamma<1$` needs its source and mathematical role. Compare an earlier method with the new one through the precise cost or obstruction each handles, not an unsupported claim that the old method simply lacked the new idea.

When a paper discusses a formalisation or companion implementation, state its actual coverage and any differences in hypotheses, domains, quantifiers, constants, or conclusions. A proved formal statement and the printed theorem may not have the same contract. Keep this disclosure separate from the mathematical exposition; do not claim exact certification from a theorem name, a successful build, or the absence of placeholders alone.

## Typeset displays deliberately

- Keep a display on one line when it fits comfortably.
- Use `align` for relation-driven chains and `multline` for one long expression paired with a short opposite side.
- In `aligned` definitions, left-align entries with a leading `&`.
- Break at the main relation sign or between additive terms, not inside a product, integrand, or tightly coupled factor.
- Use the fewest lines that remain readable. Do not strand a final additive term on its own line.
- Use `\lefteqn{}` only when it prevents a necessary bad break; preserve the local manuscript's scaffold when using it.
- Label only formulas cited later or marking a genuine hinge.
- Keep logically separate inequalities in separate displays and explain their relation in prose.
- Avoid source lines beginning with `~` and avoid manual spacing fixes unless they solve a visible typesetting problem.
- Follow the manuscript's fraction convention, for example `\frac{a}{b}` in displays and a compact slash form in prose. Preserve established compact exponent macros unless their formatting is in scope. A slash in a quotient space, set, URL, or prose is not a fraction to replace mechanically.
- Define paired constants side by side in one display separated by `\qquad`, and join paired formulas with `\quad \mbox{and} \quad`. Define derived quantities, such as their ratio, inline in the prose after the display.
- Put the quantifiers of constructed identities in the preceding prose; reserve an in-display `\forall` for standing assumptions and weak formulations.
- Write powers of evaluated functions as `\rho^2(x)` rather than `\rho(x)^2` when the manuscript does so, and keep one convention throughout.
- When `\lefteqn{}` is genuinely needed, keep the continuation scaffold exact and consistent with the manuscript. Avoid continuation lines beginning with `\times` when another structural break is possible.
- Remove dispensable transition words when they cause bad line breaks or wasted vertical space.

## Figures

For deciding whether a figure should exist, and for designing, drawing, animating and reviewing it, use the `math-figures` skill. In short: a figure is a claim. Compute it from the formulas with a script kept in the build. Say in the caption what is plotted and what is illustrative. Check what the picture implies: a region drawn as attainable must be attainable with the stated choices, and every label must name the right object. Report any parameter changed for legibility.

## Verify the finished artefact

After each accepted edit:

1. compile the smallest relevant LaTeX target;
2. inspect warnings, undefined references or citations, and overfull or underfull boxes;
3. run available lint, label, bibliography, or manuscript-consistency checks;
4. after any scripted edit, scan the sources for control bytes (`grep -lP '[\x00-\x08\x0b-\x1f]' *.tex`): a non-raw string in a script turns `\ref`, `\theta`, `\begin`, `\frac`, or `\nabla` into control characters, and the document may still compile and print "ef{...}"; always write LaTeX in scripts as raw strings;
5. after removing or renaming a label, check every `\ref` in every document that cites this one, including companions; for modular sources, check for duplicate labels with all modules compiled together;
6. inspect the affected PDF pages at readable resolution, including page breaks and neighbouring prose;
7. reread the changed passage linearly as mathematics.

Source that compiles is not necessarily finished typography. Accept an important statement or proof only after reading the rendered pages.

Reading rendered pages means looking at them. Convert the affected pages to images and view them; a log without errors is not a substitute, because bad breaks, collisions, stranded terms, and orphaned statements are invisible in the log.

### Test comprehension from the reader's text

For a substantive exposition review, first give the reviewer the actual passage, its preceding reader-facing text, and declared prerequisites. Ask for a reconstruction in their own words before consulting source notes, private notation correspondences, or writer handoffs:

- What original object is being studied, and how do the current unknowns represent it?
- Which variables and parameters are independent, fixed, or changing?
- Why is each important auxiliary quantity needed, and what does the next operation change or preserve?
- What does the result establish about the original object, and why does the next step follow?

Require exact locations where the reviewer guessed, searched backwards, or supplied an explanation from their own knowledge. Expertise is useful for detecting gaps, but a reviewer able to repair the argument mentally has not shown that the text explains it. Compare with the sources afterwards in a separate mathematical-preservation check. Scale the test to the task: a short edit needs its local context; a whole paper also needs continuous reading across section boundaries. Correct definitions, precise references, and compilation do not substitute for this test.

## Related skills

- `math-paper-campaign` — whole-paper control: building a paper from notes (statement freezing, packets, reviews) or polishing a checked manuscript through phases
- `visual-paper` — an interactive companion website built from the finished paper
- For formalising the same mathematics in Lean, see [LeanAutoformalizationSkills](https://github.com/scottnarmstrong/LeanAutoformalizationSkills)
