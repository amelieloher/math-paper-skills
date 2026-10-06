# Writing rules

Read this first when editing or drafting research-level mathematical LaTeX. It sets priorities, the hard rules, and checklists; the detailed guidance lives in the files below.

| file | governs |
|---|---|
| `writing-rules.md` (this file) | priorities, hard rules, task selection, checklists |
| `artisan-writing.md` | statements, proofs, prose, notation, introductions, displays, rendered verification |
| `house-style.md` | the default explanatory and visual target for a polished paper, with a starting preamble |

Whole-paper campaigns (building a paper from notes, or polishing a checked manuscript through phases) use the `math-paper-campaign` skill, which calls on these files for every packet.

## 1. Priority order

When guidance conflicts, the higher item wins:

1. The user's current instruction for the task.
2. Mathematical correctness and preservation of stated claims.
3. Mandatory venue requirements and the author's designated style authority. If none is designated, the house style applies to whole-paper writing and polishing.
4. Compatible local manuscript conventions and explicit project conventions, including established macros and notation.
5. The general artisan-writing guidance.
6. The assistant's own taste, only where all of the above are silent.

Corollaries: do not normalise untouched text to the guides (no churn). A request to polish a whole paper authorises moving draft prose and layout towards the selected style; the draft's existing weaknesses do not veto that. For narrow edits, preserve compatible surrounding conventions and stay within scope. Another author's conventions remain their authority. If the task is "fix a typo", fix the typo.

## 2. Safety invariants and source conventions

These mathematical safety invariants apply to every author and project:

1. Preserve established project macros and the meaning of every symbol.
2. Never remove labels, citations, or draft markers (colour-highlight macros, `[NO PROOF YET]`, `[This is a sketch.]`, and similar) unless that is the explicit task. Never polish away mathematical uncertainty.
3. Never silently change a mathematical contract. Any change in hypotheses, conclusion, quantifiers, constants, normalisation, signs, spaces, endpoints, or uniformity needs a stated proof or source and an appropriate mathematical re-check.
4. Imported or adapted material records its exact source and every change in hypotheses, constants, normalisation, notation, sign, or conclusion.

The following are default source conventions. Follow them in manuscripts that use them, and in new manuscripts. A consistent local convention or an explicit author rule may override these formatting rules, never the safety invariants above.

1. Inline mathematics is written `$...$`, never `\(...\)`. Inline mathematics that continues the preceding words is attached with `~`: `scale~$3^j$`, `by~\eqref{...}`. Do not break a prose continuation as "text, newline, `$formula$`".
2. A prose paragraph is one source block with no internal manual line breaks. A source line may begin with `$` only when the formula genuinely starts a paragraph or sits in a table or array cell.
3. Do not introduce `\[ \]`; displays use `equation`, `align`, or `multline` and their starred forms.
4. Displays end their punctuation with a thin space: `\,.` and `\,,`.
5. Use `~` before `\eqref`, `\ref`, `\cite`, and attached inline mathematics; never put a space before the `~` or begin a source line with `~`.
6. Follow the manuscript's fraction convention. A common and consistent one is `\frac{a}{b}` in displays and a compact slash form (for example a `\nf{a}{b}` macro, where defined) in running text. Do not mechanically replace quotient-space slashes, URLs, or other non-fractions.

Everything else in these guides is a SHOULD or a diagnostic. Follow it in new writing without churning untouched text.

## 3. Task selector

| task | primary guide | special care |
|---|---|---|
| drafting, polishing, or rewriting a paper | house style + artisan-writing | explain mechanisms; compare rendered pages; preserve claims and scope |
| display repair or overfull line | artisan-writing, "Typeset displays deliberately" | preserve macros; break at mathematical structure; inspect the rendered page |
| copyedit existing prose | artisan-writing | preserve claims and local vocabulary; keep the diff minimal |
| proof outline or section opening | artisan-writing, "Ideas before technicalities" | expose the mechanism; distinguish improvement from preservation; keep deferred details explicit in statements and proofs |
| technical subsection opening | artisan-writing, "Section and subsection openings" | interlace intuition with the local objects and formulas; explain comparisons and error terms |
| titles and paragraph headings | artisan-writing, "Short titles and paragraph headings" | short, concrete titles; selective bold run-in headings; keep the proof-step convention separate |
| new introduction | artisan-writing, "Build the introduction after the body stabilises" | object first; exact contribution; final version only after the body is stable |
| theorem and assumption statements | artisan-writing, "Craft statements" | quantifier order; constant dependencies; stable labels |
| regroup a multi-part proposition | artisan-writing, "Craft statements" | organise by use; keep needed intermediate estimates and labels; account for every old conclusion |
| proof sections | artisan-writing, "Write proofs artisanally" | one burden per step; point-of-use hypothesis and citation checks |
| notation and changes of representation | artisan-writing, "Keep objects recognisable" and "Test comprehension" | track the original object, variables, normalisations, and purpose |
| deferred proofs or a technical companion | artisan-writing, "Deferred proofs and technical modules" | usable statements; exact numbered proof locations; matching notation |
| figures and animations | the `math-figures` skill; artisan-writing, "Figures" | make one only when it expresses or teaches a mathematical idea; the paper's notation verbatim; check every number against the source |
| importing from another paper | artisan-writing, "Rewrite from another paper" | exact provenance; no silent strengthening; translate notation and normalisation |
| whole paper: build from notes, or polish a checked manuscript | the `math-paper-campaign` skill, then the references above per packet | bind to an exact revision; preserve frozen contracts; one canonical editor; introduction last |

## 4. Before editing

1. Read the macro definitions and the surrounding subsection, not just the target paragraph. For a full rewrite or style study, read the entire current manuscript, including proofs and consequences, and record its revision; earlier notes do not establish what an updated source says.
2. Identify the task type (table above) and the style authority.
3. Note local wrapping and display conventions to preserve.
4. Inventory labels, citations, theorem names, and draft markers in the edit region; they survive the edit unless the task says otherwise.
5. If the edit changes mathematical content, name the source supporting the change before writing.
6. If the edit adds or changes displays, keep a temporary list of every new or touched display, with its environment and purpose.

## 5. After editing

Source-format checks apply when the selected convention requires them; mathematical-preservation checks always apply.

1. No introduced line begins with `~`; no introduced prose continuation begins with `$`.
2. `~\eqref` and `~$…$` attachments are correct; no space before `~`.
3. No macro expanded; no `\[ \]` or `\( \)` introduced; display punctuation `\,.` and `\,,` present.
4. Short displays sit on one source line; long ones use `align` or `multline` sensibly.
5. Revisit the display list once the mathematics is final. For each display ask: should this be prose or inline mathematics; does it fit on one line; is the environment necessary; does every alignment point and line break do real work?
6. No label, citation, or draft marker lost; no claim strengthened without a source.
7. For substantive edits, run the manuscript's build, inspect the affected PDF pages, or state which verification was not run.
8. When the house style applies, check its explanatory and visual acceptance criteria. A polish needs explanatory revision as well as typographic consistency.
9. Check changed terminology in context, including the abstract, headings, statements, and proofs. Keep mathematical distinctions intact (a dual object need not be an adjoint operator). Keep stable labels even when their spelling differs from a new reader-facing name.
10. For substantive exposition, apply [the comprehension test](artisan-writing.md#test-comprehension-from-the-readers-text) at the task's scope, and check new explanatory sentences and table entries for truth and scope, not only the formulas.
11. After a scripted edit, scan the sources for control bytes; after removing or renaming a label, check the references in every document that cites it (see [Verify the finished artefact](artisan-writing.md#verify-the-finished-artefact)).

## 6. Uncertainty and placeholders

Draft markers are content. If a passage's mathematical status is unclear, say so to the user or leave the marker in place; prose smoothness never outranks the visibility of a gap. New text that depends on an unproved input carries an explicit marker in the manuscript's own style (for example `\red{[...]}`).
