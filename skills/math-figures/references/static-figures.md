# Static figures in the paper

## Format

- **Editable vector figures in TikZ**, using only libraries the paper already loads
  (prefer plain TikZ over pgfplots unless the paper uses it). A figure is a body file
  (`figN_body.tex`) that the paper can `\input`, plus a frozen PDF for quick
  inclusion. Keep both routes documented.
- **The paper's own macros and notation** (`\abs`, `\norm`, `\dd`, …) inside the
  figure, so a notation change in the paper is a change in one place.
- **One colour file** shared by all figures, with named roles (two families, a
  highlighted object, guides); never ad hoc colours. Colours must survive greyscale
  printing: pair colour with line style or labels.
- **Generated data** only where a picture needs it (sample paths, numerically computed
  curves), written by a script into a data directory read by TikZ. Draw everything
  else by hand, so geometry stays exact and editable.

## Building and placing

- Develop figures in a separate workspace and sync them into the paper's `figures/`
  directory with a script; do not hand-edit copies in two places.
- Keep a preview document with the paper's class, geometry and text width; check every
  figure there, not only as a large standalone image. Labels that are legible
  standalone are often too small at text width.
- Captions carry the formulas and use the paper's labels and cross-references. Write
  captions as part of the paper's prose: what is shown, then what to notice.
- Place a figure next to the passage it serves; refer to it from the text.

## Checks before integration

- Every label, symbol and number agrees with the current source.
- Exact geometry is exact: compute it (areas, crossings, positive regions) rather than
  eyeballing.
- Display constants satisfy the inequalities the figure illustrates. A barrier drawn
  with convenient constants once violated the very sign condition it was meant to
  show, while its profiles still looked ordered: check the inequality, not just the
  appearance.
- Factor slips: a one-sided change is not the range of a symmetric one; check every
  factor of two against the construction actually used in the proof.
- The figure is integrated into the manuscript only when the authors ask.
