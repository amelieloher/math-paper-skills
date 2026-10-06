# Pedagogical animations

An animation is a proof told in time. Make one only when the motion or the order of
steps carries the idea; otherwise make a figure.

## Content

- **Define every symbol on screen** when it first appears. A viewer cannot look up an
  undefined letter mid-video; one undefined symbol was enough for an author to call an
  early draft "hard to understand".
- **Chapters follow the argument**, one step each, with a banner saying what is
  happening and why ("Averaging independent copies divides the variance, so the
  fluctuation shrinks").
- **Give the essential moments time.** Slow down, or hold, at the step the idea
  depends on (the moment two terms cancel, or a bound is first gained). Give the
  central inequality or identity its own chapter, with an uncluttered picture.
- **Separate stages that do different work**, and label every frame with its stage
  (for example: a crude count gives the old exponent; a finer estimate gives the
  improvement).
- **At a threshold, show what changes**: pause on the exponent that was zero and is
  now positive, with diverging versus converging partial sums, before showing the new
  range.
- **Banners short, text large.** One line per banner, readable at normal size; move
  supporting formulas into the accompanying caption or chapter summary.
- **Proof constants are not predictions.** Constants from proofs can be absurdly large
  or small; on the moving picture they distract and read as predictions. Leave them
  off, or state beside them that they are conservative bounds.

## Illustration versus measurement

State, on screen and in the notes, what is illustration and what is measured:

- Guided or conditioned paths illustrate an event; they are not samples with their
  true weight.
- Binned quantities (a minimum over the bins of a histogram) are properties of the
  binned data, not of the underlying measures; say so.
- When the animation claims cancellation or agreement, measure the claimed quantity
  (for example the norm of the difference, computed on the plotted data), not a
  convenient proxy such as how close the curves look.
- Illustrative parameter values are labelled illustrative.

## Production

- Script every animation (for example matplotlib frames piped to ffmpeg, 1920×1080, 30
  fps, H.264 with `-pix_fmt yuv420p -movflags +faststart` so that browsers play and
  seek it), with the paper's typography (matplotlib's `mathtext.fontset: cm` is fast
  enough for per-frame text).
- The script writes the chapter times alongside the video; the player reads them.
- Seed every random element; record the parameters.
- Re-render from the script after any paper change; extract a frame at every chapter
  and check each formula, symbol and number against the final source.

## The player

- A clickable chapter list, previous/next chapter, optional pause after each chapter,
  a few playback speeds (default slightly below 1×), keyboard controls, a poster
  frame, no autoplay.
- On a website: a full-width or enlarged mode that fits one screen; chapter titles and
  summaries shown as text are claims and are checked like captions (see the
  `visual-paper` skill's [figures
  reference](../../visual-paper/references/figures.md)).
