---
name: math-paper-campaign
description: Run a careful, multi-step campaign on a complete mathematical LaTeX paper — either building it from a proof outline, notes, a formal (Lean) development, or an earlier draft, or taking an already checked manuscript through phased polishing (reduce, cite, linearise, rewrite, introduction, final audit) to a publication-ready paper. Use for whole-paper writing, rewriting, or "make this paper better" requests that need statement-by-statement control, independent reviews, ledgers, and rendered-page checks.
---

# Mathematics Paper Campaign

Own the mathematical meaning, the public statement surface, the architecture, source fidelity, the canonical manuscript, and the acceptance gates of a whole paper. Use the `latex-math-writing` skill for the prose and typesetting of every packet; this skill controls the process around it.

The governing rule: **work on one mathematical statement at a time.** Never turn an outline into a section, or a messy section into a clean one, in a single undifferentiated pass.

Carry the campaign through successive packets until the requested paper is complete. Do not stop after producing plans or review notes when the next packet is ready. Pause only for a genuine mathematical gap, a consequential author decision, missing source material, or authority the user has not granted.

## Choose the route

| Starting point | Route |
|---|---|
| a proof outline, notes, a formal development, or a draft whose proofs are not yet all written and checked | **[Route A: build](references/route-build.md)** — establish and write a correct, reviewed paper |
| a manuscript whose statements and proofs have been checked at a named revision, to be made clear and publication-ready | **[Route B: polish](references/route-polish.md)** — Phases 0–6: freeze, reduce, cite, linearise, rewrite, introduction, final audit |
| an old paper to be restructured around a new spine | Route A's [rewrite mapping](references/route-build.md#7-rewrite-an-existing-manuscript), then Route B once the mathematics is checked |

A paper built under Route A that needs substantial compression or restructuring continues into Route B from Phase 0; a paper built carefully needs only Route B's introduction phase and final audit (Phases 5 and 6). If only part of a manuscript is checked, run Route B on the checked packets and Route A on the rest, keeping the unchecked material blocked and visible.

A request for one phase or one local edit does not authorise restarting the whole campaign. A narrow edit belongs to `latex-math-writing` alone.

## What both routes share

[Shared controls](references/shared-controls.md) defines what every campaign uses:

- one canonical manuscript and one canonical editor;
- bounded statement packets, at most one load-bearing packet under edit at a time;
- a compact ledger with separate mathematical and manuscript statuses;
- the fail-closed drift protocol for any change to a frozen statement;
- independent, read-only reviewers with fresh context;
- the final publication audit and completion test.

## Style

Use the author's or venue's designated style. When none is named, use the [house style](../latex-math-writing/references/house-style.md) of `latex-math-writing`: standard article layout, Computer Modern text and mathematics, dark-blue navigation links, mechanism-first explanations. Record the style authority in the brief and include it in writing and exposition-review packets; do not reopen a settled style choice. Current instructions, mathematical contracts, venue requirements, and other authors' style authority keep their priority.

## Prohibited shortcuts

- Do not ask an agent to "fill in" or "clean up" an entire section in one pass.
- Do not write around an unresolved mathematical gap, or polish it away.
- Do not promote a diagnostic note or formal API lemma directly into the paper; do not add paper lemmas for future formalisation convenience.
- Do not use the proof author as the only referee of a load-bearing proof.
- Do not keep competing proofs or manuscripts active without an explicit reason.
- Do not accept "compiles" as evidence of mathematical or typographic completion.
- Do not write the final introduction while the principal theorem surface is still moving.
- Do not let control vocabulary (packet, ledger, gate, consumer) reach the manuscript.

## Related skills

- `latex-math-writing` — prose, notation, displays, and rendered-page verification inside each packet
- `visual-paper` — an interactive companion website built from the finished paper
- For formalising the same mathematics in Lean, see [LeanAutoformalizationSkills](https://github.com/scottnarmstrong/LeanAutoformalizationSkills)
