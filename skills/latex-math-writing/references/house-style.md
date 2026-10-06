# House style for a polished paper

This is the default explanatory and visual target for writing or polishing a research paper when the author, journal, or project names no other style. It was distilled from a whole-paper study of a published research paper in analysis. Use it as a style target, never as a mathematical authority: it prescribes no mathematics, macros, or section structure.

Current instructions, mandatory venue requirements, mathematical contracts, and another author's own style retain priority. A narrow edit stays narrow.

## Calibrate the level of explanation

- **Abstract:** the result, its meaningful setting and dependence, the principal consequences, and a concrete mechanism. Include a secondary technical detail only if the reader can understand why it matters.
- **Introduction and proof outline:** explain the obstacle and the ideas resolving it. Keep the final objective distinct from preparatory bounds; compare old and new arguments through their actual costs. Navigation references conclude an explanation rather than replace it.
- **Section entrance:** orient the reader in one or two sentences, then explain why the section's argument works. Use intuition first, but keep a familiar mathematical object when it clarifies the point. Avoid input tuples and repeated lists of constant dependencies.
- **Subsection entrance:** combine the local idea with the actual quantities and one or two useful relations. Identify the operation, the gain, and its error. Do not abbreviate away essential indices or replace the explanation with equation references. If the subsection opens directly with a proof, its opening paragraphs can do this work.
- **Statement:** the full contract, organised by the conclusions the reader needs. Interpretation goes outside the environment. A shorter statement can keep necessary subsidiary estimates in the proof, with their labels and uses intact.
- **Proof:** expose the mathematical action, explain terms when they enter, and close each subgoal. Use a brief route for a long proof and `\emph{Step 1: Description.}` for its numbered stages; keep short proofs short. A short final assembly proof that fixes parameters in dependency order, applies the accepted inputs, and stops is often the clearest.

For a generic averaging argument, a section might explain: "Averages reduce randomness, but the object we want to estimate is not itself that average, so we also control their discrepancy." A subsection can then define the average and use its variance identity to quantify the gain, while naming the estimate for the discrepancy. These are two levels of one causal explanation, not a prose version followed by a formula-only version.

## Distinctions that make the explanation work

These are reusable questions, not requirements to add particular machinery to unrelated mathematics.

1. **Name the target and the intermediate errors separately.** Say what an estimate does not yet prove when that prevents a likely misunderstanding. Concentration of two quantities around their means does not show that the means are close.
2. **Separate improvement, preservation, and cost.** One step may establish smallness, another may use it, and changing a construction may consume some of it. Explain the actual source of the reserve. Restarting a construction does not erase its earlier errors.
3. **Explain failure without pretending it is free.** A failed test may supply compensating information while the errors grow. Explain the growth bound, the decreasing quantity that pays for it, and any overlap or comparison cost.
4. **Explain why related measurements coexist.** When several quantities track related effects (an additive loss, a weighted cumulative history, successive increments), say what each measures, why each is needed, and what converts one into another, such as summation by parts. Name the purpose of the conversion, not only its name.
5. **Make geometry concrete.** Describe shapes, directions, and costs before an abstract metric. In a combined progress count, distinguish the reference state fixed at initialisation from the current one. A coordinate change changes the equation and norms in a specified way; it does not remove dependence on the original domain.
6. **Explain the terms of an estimate.** Identify which term comes from averaging, which from a discrepancy, which from the boundary, and which from earlier scales. Say why the decay beats the growth and where the relevant assumption is used.
7. **Preserve information while changing presentation.** When a multi-part proposition is regrouped by use, its subsidiary estimates stay in the proof as labelled conclusions. Every old conclusion and later use must remain accounted for.
8. **Finish the logical transfer.** Identify the extra equation, comparison, absorption, limiting argument, or common-event construction that turns the prepared estimates into the claimed theorem. Do not stop at "apply the estimate" or "use a cutoff argument": a cutoff is a tool; the explanation is what it allows you to compare.

The detailed editing procedure is in [artisan-writing.md](artisan-writing.md), and its phase-by-phase application to a whole paper is in the `math-paper-campaign` skill ([Route B](../../math-paper-campaign/references/route-polish.md)).

## Terminology and source conventions

- Use an established mathematical name consistently, and choose names by what the object measures. The defining formula, not a verbal analogy, governs.
- A terminological preference does not authorise renaming a different mathematical object (calling a variational pair "primal–dual" is not a licence to rename the adjoint operator).
- Identify a "response," "recurrence," "loss," or "transfer" through the energy, quantity, or comparison it denotes before relying on the word.
- Write the full meaningful expression with its identifying indices rather than undefined shorthand. Prefer an explicit object to a one-use alias. Declared proof-local abbreviations remain useful.
- Refer to published work by its bibliography key and, where needed, an exact result locator; never by a floating nickname. An earlier draft is evidence to inspect, not a citation.
- Use `$...$` inline, ties before attached formulas and references, and the manuscript's macros. Use `equation`, `align`, or `multline` according to the mathematical shape.
- Keep short, concrete titles and selective bold `\paragraph{Title.}` headings, as in [Short titles and paragraph headings](artisan-writing.md#short-titles-and-paragraph-headings).

## Finished-page profile

- `article` class at 11 points on US Letter with 1.05-inch margins, standard Computer Modern text and mathematics. Preserve meaningful special alphabets; do not swap ordinary symbols or fonts to imitate another paper.
- A centred standard title and author block, affiliation footnotes, no displayed date, and a compact abstract, using the paper's real metadata.
- Bold, left-aligned numbered sections and subsections at standard article sizes; no centred small-capital headings or run-in subsections by default.
- Bold run-in `\paragraph{Title.}` for distinct explanatory parts where a heading helps; italic numbered proof steps as a separate convention.
- Justified single column, 1.25-em paragraph indent, zero global paragraph skip. Small local skips separate real explanatory phases only.
- A small running title at the upper left and the page number at the upper right, with a thin header rule; the title page uses the plain style.
- For a long paper, a section-level table of contents after the abstract, with the introduction on a fresh page.
- Dark-blue navigation colour `paperlink` (RGB 0,0,114, `#000072`) for contents entries and page numbers, all `\ref` and `\eqref` links, citations, and URLs, with `colorlinks=true` and `linktoc=all`. Colour the navigation, not the mathematics.
- Lettered principal theorems in the introduction where useful; section-numbered propositions and lemmas in the body, with bold labels, italic statements, italic proof openings, and square end marks; equations numbered by section at the right. Preserve the numbering and labels of an established manuscript.
- Ordinary-size displays, one line where they fit, aligned calculations broken at mathematical structure. Keep prose close to the display it introduces or interprets; never shrink equations to fit.

## Starting preamble

For a new standalone paper, start here and add only the mathematical packages and environments the paper needs. In an existing manuscript, merge settings into its preamble without loading packages twice.

```latex
\documentclass[11pt,letterpaper]{article}
\usepackage[T1]{fontenc}
\usepackage{amsmath,amsthm,amssymb}
\usepackage[margin=1.05in]{geometry}
\usepackage{microtype}
\setlength{\emergencystretch}{1em}
\usepackage{xcolor}
\definecolor{paperlink}{RGB}{0,0,114}
\usepackage{hyperref}
\hypersetup{colorlinks=true,linktoc=all,
  linkcolor=paperlink,citecolor=paperlink,urlcolor=paperlink,pdfstartview=Fit}
\usepackage{enumitem}
\setlist[itemize]{leftmargin=2em,itemsep=0.25em,topsep=0.35em}
\setlist[enumerate]{leftmargin=2.25em,itemsep=0.25em,topsep=0.35em}
\setlength{\parindent}{1.25em}
\setlength{\parskip}{0pt}
\usepackage{fancyhdr}
\pagestyle{fancy}
\fancyhf{}
\fancyhead[L]{\small Short manuscript title}
\fancyhead[R]{\small\thepage}
\setlength{\headheight}{14pt}
\numberwithin{equation}{section}
\setcounter{tocdepth}{1}
\date{}
```

Replace the running-title placeholder and set the real title, authors, and PDF metadata. For a long paper, put `\tableofcontents\clearpage` after the abstract. Remove any conflicting `hidelinks` option or later colour overrides.

## Acceptance

Compare the title, abstract, and contents page, an introductory theorem page, a dense proof page, and a section transition against this profile. Check fonts, headings, white space, headers, equation widths, and link colours in the rendered PDF, and read the same passages for concrete motivation, useful proof orientation, explicit dependencies, and concise closure. Compile until references settle and inspect the actual pages and link destinations. A whole-paper polish still needs the every-page review; representative comparisons do not replace it. Report any check that was not performed.
