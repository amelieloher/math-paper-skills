---
name: math-figures
description: Design, build and review figures and animations for mathematical papers and their companion websites — editable TikZ figures in the paper's notation, interactive figures, and pedagogical animations — under one rule, that a visual earns its place only by expressing a mathematical idea or teaching one. Use when proposing, drawing, revising, reviewing or animating any figure for a mathematical manuscript, talk or visual paper, or when deciding whether a figure should exist at all.
---

# Mathematical Figures and Animations

**A figure or an animation has value only if it adds mathematical insight or is
pedagogical. Otherwise it is useless.** It is never an aesthetic addition. Every
visual must express one mathematical idea that the text states and the picture makes
immediate: a mechanism, a geometry, a comparison of scales, the order of steps in a
proof. A visual that only decorates, restates a formula as a shape, or shows that
something "looks nice" is not made, however attractive. Remove a figure that fails
this test even if it is finished.

## Workflow

1. **Understand the step.** Read the proof or argument the visual would serve until
   you can state what it does and why it works.
2. **State the idea in one sentence** and the question the visual answers ("why is the
   error term small after this step?"). Record both in a figure-notes file before
   drawing anything.
3. **Apply the value test** of [value and design](references/value-and-design.md). No
   idea, or an idea the text already makes immediate: no figure.
4. **Design the encoding**: what each visual element stands for, which parts are
   exact, which are schematic, which are illustrations (simulated or sample data), and
   where the formulas go (usually the caption, not the drawing).
5. **Build**: static paper figures as editable TikZ in the paper's notation ([static
   figures](references/static-figures.md)); animations as scripted videos with
   chapters and banners ([animations](references/animations.md)); figures for a
   website per the `visual-paper` skill's [figures
   reference](../visual-paper/references/figures.md).
6. **Check against the source**: notation verbatim, every number, sign, factor and
   constant, rendered at the real text width.
7. **Independent review** with the concrete checklist in
   [review](references/review.md); record each correction and why.
8. **Author approval.** A figure is finished only on the authors' word. Integrate it
   into the manuscript only when asked; never edit the paper otherwise.

## Non-negotiable rules

- **One idea per visual**, stated in words before drawing; several ideas need several
  panels or several visuals.
- **The paper's notation, verbatim**, through its own macros; no symbol that the paper
  does not define, and none left undefined in the caption or on screen.
- **Never show more than the paper proves.** Draw the paper's bounds as uniform upper
  bounds, not fitted rates or envelopes that paths need not respect. Mark examples as
  examples.
- **Separate exact from schematic from illustration**, in the figure notes and on the
  page ("schematic"; "numerical illustration"; "illustrative value of ε").
- **Measure what you claim.** If a visual claims a quantity is small or two curves
  agree, compute that quantity, not a proxy.
- **Readable where it will be read**: check at the paper's text width, in print and on
  screen, and for animations at the speed a viewer reads.

## When the paper changes

Figures and animations go stale silently. After any revision re-check every symbol,
number, theorem number and claim against the final source, and fix the source (script
or TikZ), never only the output.
