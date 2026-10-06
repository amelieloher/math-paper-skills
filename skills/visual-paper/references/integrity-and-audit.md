# Integrity controls and the audit loop

Two kinds of text reach the reader, and each has its own controls.

## Paper text: verbatim by construction

- **C1 Anchors.** Content never contains paper text, only anchors with a span hash;
  the build extracts the text from the pinned source.
- **C2 Deterministic TeX.** One macro table plus a render harness that fails on any
  KaTeX error or unknown macro. For a cited external paper, use its own macro table:
  never render its text with the main paper's macros or notation popovers.
- **C3 Proof steps.** Steps are cut positions inside the proof span; a check asserts
  the steps concatenate exactly to the proof (no gap, overlap or reordering).
- **C4 Staleness.** A source revision re-pins the source and re-resolves anchors;
  every node whose spans changed is marked stale and its verdicts voided.

## Agent text: cited, then independently audited

- **C5 Sentence-level citation.** Every sentence of summaries, ideas, step titles,
  titles, notation glosses and figure specs is a claim with cites. The schema rejects
  an uncited claim, a symbol absent from the notation table, and a numeral or
  exponent that does not occur verbatim in a cited span.
- **C6 Independent blind audit.** The auditor is from a different model family than
  the writer. It receives only a script-generated packet: the cited spans (extracted
  by script) and the claims, with no writer notes. It first writes its own summary
  of the spans (stage one, recorded before the claims are released), then judges
  each claim: `supported | imprecise | unsupported | contradicted`. Only `supported`
  publishes. Auditors report; writers fix; a different auditor re-audits.
- **C7 Dependency links.** See [dependency graph](dependency-graph.md).
- **C8 Canaries.** Planted errors — flipped inequality, dropped hypothesis, wrong
  exponent, swapped quantifiers, primal/dual swap — look identical to real claims.
  Their key lives outside the repository. Before any real audit, each auditor must
  catch every canary in a trial packet (Gate T); afterwards plant some in about one
  packet in five. A missed canary sends that auditor's batch to another auditor. The
  build refuses to publish if canary text is present in content. Never describe the
  canaries to any agent.
- **C9 Ledger, fail-closed.** Each verdict is bound to (node id, claim id, sha256 of
  the cited spans, sha256 of the claim text, auditor, date, packet). Editing either
  side voids it. The publish check fails unless every published claim has a current
  `supported` verdict.

Audit checklist given to every auditor: quantifiers and their order; dropped or
weakened hypotheses; direction and strictness of inequalities; exponents, constants
and their dependencies; primal versus dual; which domain, cube, grid or scale; dropped "up
to" qualifiers; over- or understatement; a result attributed to the wrong source.

Escalation: disagreement between a writer's revision and an auditor, or between two
auditors, goes to a third blind auditor; still unresolved goes to the authors.

## Author gates

The authors review the section map and its links, every adjudicated item, a random
sample of at least 10% of result-level claims per section (and one node per
subsection), every figure spec and every finished figure.

## Practical lessons

- **Two-stage dispatch matters.** Release the claims only after the auditor's own
  summary is written; otherwise "own summary first" is not enforced.
- **Measure auditor recall** on the trial packet and fix the packet prompt until
  recall is 100%. Report honestly which rounds had contradicting verdicts.
- **Author waivers.** When the authors direct that edits be published without a new
  audit (for example after the final revision of an already audited paper), record a
  ledger entry with auditor `author-waiver` and a named packet, never an auditor's
  name. Restore, rather than waive, every earlier verdict whose claim and span
  hashes still match. Write the list of waived claims to a report for the authors,
  and do not count the waiver as an auditor anywhere on the site. Tell the authors
  if the site's description of its checks ("checked by an independent auditor") no
  longer covers every claim.
- **Citation checks.** For each pointed citation of an earlier paper, have an auditor
  check that the cited item supports the use. Mismatches (wrong section numbers,
  results cited under the wrong number) go to the authors as paper-level notes.
