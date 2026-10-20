# A paper from a completed formalization

Use this with Route A when the mathematics already exists as a checked formal development (for example in Lean) and
the task is a readable paper for human readers. The formalization settles correctness; the campaign's risk is
the opposite one: a text that transcribes the formal development, explains nothing, and grows without limit.
Learned on two campaigns (2026); every rule below answers a failure that happened.

## The orchestrator is the editor

- The orchestrator does not write the paper. Writers draft packets; the editor chooses the level of detail, sends
  back drafts that overrun, or cuts them to size. A campaign whose supervisor decides to "write every detail"
  produces a document several times too long, whatever the page target says.
- Every brief carries a hard page allowance per section and the rule "over the allowance = not done". Measure
  pages as drafts land, and stop to cut immediately, never "later". A late pass that adds tens of pages to fix a
  presentation problem is a failure even when each addition is defensible.
- A dedicated level-of-detail critic (a fresh reviewer whose only job is the detail standard) is worth having.

## Write a detail standard before writing

Fix, in one short file, what is written out and what is not, for a named reader (e.g. "a PDE analyst who has read
the proof map, checking each step with pen and paper in reasonable time"):

- **One line or a citation:** standard inequalities and embeddings, well-posedness of standard problems, geometric
  series, constant bookkeeping (one sentence on dependence), cases identical by symmetry, a second instance of an
  argument already given, routine measurability, passing between weak formulations and representatives.
- **Written out:** every estimate specific to the construction, with the mechanism that makes it true; claimed
  uniformities; exact identities on which cancellations rest; the order in which parameters are chosen where a
  later choice depends on an earlier one; where smallness comes from and which loss it pays for; every place where
  the formalization showed the source to be wrong or incomplete (the corrected statement, without its history).
- **Never:** formalization scaffolding (predicates, packaging structures, case splits that exist only for the
  proof assistant), formal declaration names in place of proofs, several variants of one lemma for different
  users, "for completeness" passages, constants whose value is never used.
- For routine verifications repeating one pattern many times, prove one representative case, say why the others
  are identical, and point to the formal declaration that checks all of them; never for a main estimate.

## A map of the proof first, then a pilot

- Write first a self-contained outline of the proof (a "proof map": the construction, the main results, the
  reduction, the induction or iteration and its pieces, each with a precise statement and the idea of its proof).
  Many readers read only this part; it deserves the most care and the author's detailed calibration.
- The narrative never states anything simplified or false: precise statements, intuition outside them, every
  intuitive sentence literally true.
- Then write one technical section as a pilot and let the author calibrate it. Roll the rest out at the pilot's
  quality, one section at a time (or in parallel only if quality does not suffer).
- Turn the author's calibration comments into a binding style file at once, generalized from the examples the author
  gives, and run every later draft past an auditor that checks it against that file.

## Claims and the formal development

- The paper claims nothing that the formalization does not prove. If the formal statement is weaker, write the
  weaker form; if a natural reader-facing form is weaker than the formal one (a bound in $L^\infty$ in time where the
  formal statement gives every time), that is allowed. Stronger, never.
- A proof may compose formally proved statements by elementary steps (an induction, a chain of inequalities) even
  where the formal proof composes them differently; every statement it uses must be formally proved.
- Keep a correspondence table, published with the formalization, mapping every numbered statement and display of
  the paper to the formal declarations (direct, weakening, composition, cited, none), pinned to one commit of the
  formal development, with the paths and lines at that pin. Re-pin it at every later change of either side.
- Keep the paper-facing formal statements in the formal development even when the top theorem does not use them:
  a dead-code sweep of the formal development otherwise deletes them, and the table loses its rows. Protect them
  as roots of every later sweep.
- The paper says what is formalized, where, at which version, with which axioms, and who (which people and which
  AI systems) did what.

## Reviews that found real problems

- Several independent fresh readers of the whole paper, each asked whether it is self-contained and makes sense.
- A fresh reader looking only for proofs that describe a proof without doing it; expand those on the margins, with
  a stated bound on the growth.
- A whole-paper notation audit at the end: unnecessary symbols, a symbol with two meanings, visually similar
  symbols, notation that hides an index.
- After any language or style pass, a line-by-line check of the new explanatory sentences against the proofs: an
  editor produces roughly one false explanatory sentence per ten to fifteen pages, which only such a check finds.
