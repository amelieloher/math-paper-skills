# External sources and Lean

## A cited earlier paper

Many papers rest on an earlier paper through citations such as
`\cite[Lemma~2.15]{X}` and bare `\cite{X}`. Two tiers make these inputs visible.
Get the authors' approval for each tier; tier 2 adds mathematics to the site.

- **Tier 1: cited items, quoted exactly.** Pin the earlier paper's TeX (its arXiv
  version), compile it once for its own `.aux`, and extract its own span index and
  macro table. Every pointed citation that names a numbered item becomes an external
  node quoting that item verbatim, with its own number and version stated. Link its
  proof by location or quote it when short. Resolve citations mechanically by number
  **and** kind (a "Proposition 2.15" is not "Lemma 2.15"); anything unresolvable goes
  to a curated override map keyed by line and locator, never guessed in code.
- **Tier 2: background nodes.** For a bare citation that uses a property of the
  earlier paper's objects, a writer drafts a background node: claims citing the
  earlier paper's spans that establish it and the main paper's line where it is
  used. Show a visible "Background: not stated in this paper" badge; audit it
  exactly like other claims.
- **Paper-level citation check.** Have an auditor confirm each pointed citation
  supports its use. Report mismatches (wrong section number, a numbered item that
  does not say what is used) to the authors; do not fix them on the site.
- When the main paper is revised, citation line numbers move: remap the override map
  and each background node's `used_at` lines (by unique context around each cite),
  and check that every bare citation is still covered.

## Lean formalisation

- Vendor the Lean repository's correspondence file (paper item ↔ declaration ↔
  file ↔ status) at a pinned commit in `SOURCE.lock`. Link badges to the declaration
  at that commit so that later history does not break them. Do not rewrite that
  commit's history.
- Match rows by the paper label quoted in backticks, then **re-key by graph node**:
  a label that is a node id badges that node; a label in section prose badges the
  content node whose statement contains it (e.g. a definition); a label that reaches
  only a section or subsection badges nothing.
- Rows that formalise a step of a proof ("used near X", "used in X") badge nothing.
  Rows that name an item only in words go to a small hand-kept map (declaration →
  node, with a reason); leave unmatched anything that is not a paper item (a
  satisfiability witness, a consistency lemma).
- Show the check where readers look: a green check on each formalised box in the
  graph and in the phone outline, a legend entry, and a green badge above the
  statement linking to the declaration. A badge only inside the reading panel is
  easily missed.
- Lean links fail for readers until the Lean repository is public; coordinate the
  timing with the site launch. An optional auditor check compares a node's statement
  summary with its Lean statement; it never replaces the paper as the reference.
