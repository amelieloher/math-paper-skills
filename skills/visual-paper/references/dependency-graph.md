# The dependency graph

Readers navigate by the graph, so its links must be complete and correct. The
convention readers expect: **an arrow A → B means "A is used to prove B"** (or to
state or define B). Store edges as "B uses A" and draw them reversed.

## Levels

- **L0**: sections and the main theorems. Keep the main theorems at L0 with no parent
  even though their statements sit in the introduction.
- **L1**: subsections (open a section to see them).
- **L2**: results — lemmas, propositions, inline definitions, key labelled estimates,
  named claims inside proofs. Most of these have no environment; identifying them
  needs judgement and is audited.

Section-to-section and subsection-to-subsection arrows are **never hand-authored**:
there is an arrow from box X to box Y exactly when some result inside Y uses some
result inside X. Lift them mechanically from the result-level `uses`.

## Curating `uses`

1. **Baseline**: the mechanical `\ref`/`\eqref` graph of the node's statement and
   proof.
2. **Drops**: a baseline reference that is not a real dependency (a remark, a pointer
   to a later use, a hypothesis display whose proposition is already linked) goes in
   `dropped_refs` with a one-line reason. A check fails on any baseline reference that
   is neither used nor dropped.
3. **Additions** (`origin: added`): a dependency used without `\ref` — by name ("the
   adapted cube bound"), through notation (a definition whose symbol appears), or an
   assumption the proof invokes ("by stationarity"). Anchor each addition to the words
   that show the use and give the reason.
4. Audit adds and drops like claims.

## Build rules learned the hard way

- **Proof homes.** When a result's proof sits in a different box than the result
  (a main theorem stated in §1 and proved in §5.4; a proposition stated in §2 and
  proved in §4.4), the proof's box is otherwise empty and the proof's inputs point
  past it. For such a node, let its proof's box use everything the proof uses (the
  uses whose anchor lies in the proof span), let the result use that box, and mark
  the result's own proof edges so that the map draws them through the box. Keep the
  full list in the reading panel.
- **Prose references are not dependencies.** A `\ref` in section or subsection prose
  is a roadmap or forward pointer ("we prove Proposition 2.1 in Section 4", "this
  yields Theorem B"); drawing it as an arrow often points the wrong way. Do not draw
  edges from section or subsection prose.
- **Labels in prose resolve to their definition.** A labelled display inside a
  definition paragraph resolves mechanically to the enclosing subsection. Resolve it
  instead to the smallest content node whose statement contains the label; skip it if
  that is the citing node itself.
- **No self-loops or cycles.** Run an acyclicity check on the curated graph; a
  mechanical reference kept by mistake can create a false cycle.

## Auditing the links end to end

Do this once the content is complete and again after a major revision. Split the
nodes into about four groups by section; give each auditor a read-only brief with a
reference table (every node's id, kind, number, title, parent box, statement and
proof lines; every label with the node a reference to it lands on). For each node the
auditor reads the statement and whole proof and reports, with a quoted line of the
source for each finding:

- missing links (used by name, through notation, or an assumption invoked);
- wrong links (unused, wrong target, reversed);
- wrongly dropped references;
- clearly wrong placement.

Fix systematic problems in the build (as above) before adding links one by one; then
apply the missing links with a script that anchors each to the quoted evidence. On
a real build, the first end-to-end audit found dozens of missing links and many
links to whole subsections that belonged to definitions. Such an audit can also find
gaps in the paper itself, for example an inequality used without reference. Report
such gaps to the authors.
