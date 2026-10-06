# Value and design

## The value test

Before drawing, answer in writing:

1. **What is the one idea?** One sentence, in the paper's terms.
2. **What question does the visual answer** that a reader of the text would ask?
3. **Why a picture?** Name what the picture shows that the text alone does not make
   immediate. Visuals earn their place by showing one of:
   - a **mechanism**: how a quantity is produced (an error term *is* the area between
     two curves; a cancellation comes from two contributions of opposite sign);
   - a **geometry**: where something lives, which faces of a domain matter, how a
     change of variables turns a level set into a slice;
   - a **comparison of scales or rates**: linear versus quadratic variation at two
     points, giving two different powers;
   - **the order of a proof**: decompose, estimate each piece, then sum;
   - **what changes at a threshold**: an exponent that was zero becomes positive;
   - or it **teaches**: an orientation or notation-setting picture (the scales of a
     domain, the faces of its boundary) that lets a reader follow the next step.
4. **Would a reader understand the idea faster or more correctly with it?** If not, or
   if the visual is decoration, a formula drawn as a shape, or a picture of the
   statement rather than of the reason, do not make it.

Record the answers in a figure-notes file (one section per visual: the quantity, the
point a reader must see, the encoding, what is exact). Read the notes before changing
a visual; update them with every correction.

## Designing the encoding

- **Lead with the point.** Arrange panels in the order of the argument; number the
  steps when the reading order matters. A panel order that runs against the proof is
  the first thing readers notice.
- **Encode the decisive fact visibly**: shade the area that equals the error term;
  mark the single point where two curves cross; draw only the region where the
  estimate is used. If the decisive fact is a sentence, put that sentence next to the
  picture.
- **Formulas go in the caption**, not in the drawing, unless a formula is the point. A
  dense formula inside a panel competes with the picture and is unreadable at text
  width.
- **Distinguish curves individually**: contrast plus a label for each, not a colour
  legend alone.
- **Exact, schematic, illustration.** Say which geometry is exact (supports, signs,
  zero crossings, an exact area), which proportions are schematic (widths not to
  scale), and which data are illustrations (simulated paths, binned counts).
  Illustrative constants are labelled as such.
- **Bounds are bounds.** A paper's estimate is an upper bound uniform over a class;
  draw it as a reference curve, never as a fit to sample data; choose the reference
  constant so that it visibly bounds the plotted example, and label it illustrative.
- **No false envelopes.** Typical scales are not envelopes: do not draw curves that
  every path is supposed to respect unless the paper proves it.
- **Projections are labelled**: a projected area is not a volume in the full
  variables.

## Choosing the medium

| The idea is… | Use |
|---|---|
| a static mechanism, geometry or comparison | a TikZ figure in the paper |
| a dependence on a parameter the reader should vary | an interactive figure (website) |
| the time order of a construction, or motion itself (one phase finishes while another continues) | an animation |
| a simulated phenomenon the reader should see vary | a runnable figure with "new sample" and a visible seed |

An animation is justified only when motion or order carries the idea; otherwise make a
figure.
