---
name: latex-math-writing
description: Draft, edit, refactor, and publication-polish research-level mathematical LaTeX with economical statements, complete proofs, stable notation, source fidelity, readable displays, and rendered-page verification. Use for notes, papers, slides, theorem and proof writing, display repair, or turning a mathematically checked manuscript into a clear publication-ready paper without changing its claims.
---

# LaTeX Mathematics Writing

Write for a mathematically sophisticated reader who knows the field but not the project's development history. Produce finished mathematical prose, not a transcription of notes, formal proof code, review reports, or project-management language.

## Route the task

Read [references/writing-rules.md](references/writing-rules.md) first: it fixes the priority order, the mathematical safety rules, and the source conventions. Then load only what the task needs:

- [references/artisan-writing.md](references/artisan-writing.md) for statements, proofs, prose, notation, introductions, displays, adaptation from other sources, and rendered verification;
- [references/house-style.md](references/house-style.md) for the default explanatory and visual target of a polished paper, including a starting preamble; use it for whole-paper writing and polishing unless the author or venue prescribes another style.

For work on a whole paper, also use the `math-paper-campaign` skill: building a paper from notes or an outline, or taking a checked manuscript through the phased polish (reduce, cite, linearise, rewrite, introduction, final audit). That skill controls packets, ledgers, review, and integration; this skill controls the reader-facing mathematics, prose, and TeX.

## Establish authority before editing

1. Read the canonical TeX entry point, macro file, bibliography, surrounding section, and any style example the author designates.
2. Identify the exact mathematical source and its status. For a rewrite of a checked manuscript, bind the work to the named revision and the scope of that check.
3. Inventory local notation, theorem environments, labels, citations, references, display style, and visible uncertainty markers.
4. Apply the priority order in the writing rules. When no other style authority is named, the house style is the target for whole-paper polishing: move draft prose and layout towards it while preserving mathematical contracts, meaningful notation, and venue requirements.

Do not normalise untouched text merely to enforce a house rule. Preserve established macros and symbols. Resolve a genuine notation conflict before writing; never change an object's meaning to simplify notation.

For a whole-paper rewrite or style study, read the entire current manuscript, including proofs and consequences, before inferring its strategy. Bind that reading to a revision; the author's updates supersede earlier editorial diagnoses. For a narrow edit, read the relevant dependency context without restarting a full publication campaign. Check repository state before editing shared files and synchronise without overwriting others' changes; commit or push only when authorised.

## Preserve the mathematical contract

- Never silently strengthen, weaken, specialise, or generalise a claim.
- Keep hypotheses, conclusions, quantifier order, spaces, boundary conditions, normalisations, signs, exponents, exceptional sets, constant dependencies, and uniformities fixed unless a mathematical review accepts the change.
- Preserve labels, citations, draft markers, and explicit uncertainty unless their removal is authorised and mathematically justified.
- A mismatch with a formalisation (for example in Lean) is evidence, not permission to edit the paper's contract. Pause the affected work and reopen its review.
- Replace a proof step by a citation only after checking the source's exact result, location, hypotheses, conclusion, normalisation, and transport to the present setting.
- Do not hide a load-bearing step behind "standard," "clear," "straightforward," or "similarly." Prove it or cite it precisely.

## Write the mathematics artisanally

- Put only the mathematical contract in a theorem-like environment. Keep purpose, intuition, provenance, and strategy in the surrounding prose.
- Give each paragraph or named proof step one coherent mathematical burden: a reduction, construction, theorem application, decisive calculation, or subgoal-closing consequence.
- Explain the obstruction before its correction, and the mathematical consequence after a decisive display. In a long construction, make the remaining error and the preserved properties explicit.
- For abstracts, outlines, and section openings, follow [Ideas before technicalities](references/artisan-writing.md#ideas-before-technicalities): explain the mechanism before the parameter list, distinguish improvement from preservation, and check that every deferred condition remains explicit somewhere.
- Calibrate [section and subsection openings](references/artisan-writing.md#section-and-subsection-openings): sections give the intuitive strategy; subsections interlace that intuition with the precise objects, formulas, and comparisons used next.
- Follow [Short titles and paragraph headings](references/artisan-writing.md#short-titles-and-paragraph-headings): short, concrete titles and selective bold `\paragraph{Title.}` headings for distinct explanatory parts, kept separate from the italic proof-step convention.
- Begin a proof paragraph with the mathematical action it performs. Put a brief route map before a long proof.
- Introduce an object immediately before its first sustained use, explaining its kind and job. [Keep objects recognisable through the argument](references/artisan-writing.md#keep-objects-recognisable-through-the-argument) across differentiation, normalisation, coordinate changes, and decompositions. Name a repeated expression only when the name lowers reader effort or reveals structure.
- Cite accepted inputs at the point of use and say why their hypotheses apply.
- For [deferred proofs and technical modules](references/artisan-writing.md#deferred-proofs-and-technical-modules), give the usable statement, its role, and its exact proof location in matching notation.
- Give every major result distinct motivation before it and a useful plain interpretation afterwards. Do not paraphrase its display merely to repeat it.
- Distinguish the final objective from preparatory errors, and improvement from preservation or controlled growth. Account for the cost of failed steps rather than calling them free progress.
- When reorganising a proposition, group the conclusions by use while keeping necessary labelled intermediate estimates in the proof. Check every old conclusion and downstream use.
- Use simple verbs and exact mathematical nouns. Remove development nicknames, praise, slogans, and ornate transitions.
- Stop when the assertion is proved.

## Whole-paper rewrites

A complete rewrite or polish of a paper is a campaign: follow the `math-paper-campaign` skill ([Route B](../math-paper-campaign/references/route-polish.md) for a checked manuscript). Keep one canonical manuscript and one canonical editor; reviewers inspect exact read-only packets and return evidence, findings, and the smallest repair.

## Typeset and verify

- Follow the selected style authority and compatible local conventions. Keep a display on one line when it fits; break at mathematical structure, not inside a coupled product or integrand.
- For a new standalone paper with no prescribed style, start from the [house style](references/house-style.md#starting-preamble) preamble and compare representative rendered pages with its profile.
- Reuse existing macros, labels, theorem styles, and reference commands. Follow the manuscript's fraction and terminology conventions without blind search-and-replace.
- Compile the smallest relevant target after substantive edits.
- Check errors, references, citations, warnings, and overfull material introduced by the change.
- Convert the affected PDF pages to images and look at them at readable resolution, including neighbouring prose and page breaks.
- Reread the changed passage linearly as mathematics and apply [the comprehension test](references/artisan-writing.md#test-comprehension-from-the-readers-text). Compilation alone is not publication verification.

Report any unresolved mathematical status, skipped verification, meaningful warning, or required author decision plainly.
