# Mathematics Paper Skills

Agent skills for writing research-level mathematics in LaTeX, for making figures and animations that express a mathematical idea, and for turning a finished paper into an audited, interactive "visual paper" website. They work with Claude Code and OpenAI Codex: each skill is a folder whose `SKILL.md` is read by both, with optional `references/`; `agents/openai.yaml` is Codex-only interface metadata.

## Skills

| Skill | Use it for |
|---|---|
| [`latex-math-writing`](skills/latex-math-writing/) | drafting, editing, and publication-polishing mathematical LaTeX: statements, proofs, notation, introductions, displays, and rendered-page checks |
| [`math-paper-campaign`](skills/math-paper-campaign/) | whole-paper work, one statement at a time: **build** a paper from notes or an outline, or **polish** a checked manuscript through phases (reduce, cite, linearise, rewrite, introduction, final audit) |
| [`visual-paper`](skills/visual-paper/) | building a companion website from a paper: proof dependency graph, exact statements and proofs quoted from the source, audited summaries, notation cards, figures, and Lean badges |
| [`math-figures`](skills/math-figures/) | designing, drawing, animating and reviewing figures for papers and websites, made only when they express or teach a mathematical idea |

`latex-math-writing` is the entry point for any writing task. Its references:

- `writing-rules.md`: priorities, hard rules, and checklists (read first);
- `artisan-writing.md`: the detailed guidance on statements, proofs, prose, notation, and typesetting;
- `house-style.md`: the default look and explanatory style of a polished paper, with a starting preamble.

`math-paper-campaign` controls the process around it for a whole paper:

- `route-build.md`: from notes, an outline, or a Lean development to a correct, reviewed paper;
- `route-polish.md`: Phases 0–6 that turn a checked manuscript into a publication-ready one;
- `shared-controls.md` and `control-artifacts.md`: packets, the ledger and statuses, the drift protocol, reviewers, and the final audit.

## Examples

Visual papers built with these methods:

- [Homogenization at a polynomial scale in high contrast](https://scottnarmstrong.github.io/hcp-visual-paper/) (Armstrong, Kuusi, Loher)
- [Döblin–Fourier cancellation and kinetic Aleksandrov estimates](https://amelieloher.github.io/DF-visual-paper/) (Loher, Mooney, Mouhot)

For formalising mathematics in Lean, see the companion collection [LeanAutoformalizationSkills](https://github.com/scottnarmstrong/LeanAutoformalizationSkills).

## Installation

Clone the repository and link each skill into your agent's skills directory:

```bash
git clone https://github.com/amelieloher/math-paper-skills.git
cd math-paper-skills

# Claude Code
mkdir -p ~/.claude/skills
for s in skills/*; do ln -sfn "$(pwd)/$s" ~/.claude/skills/"$(basename "$s")"; done

# Codex
mkdir -p ~/.agents/skills
for s in skills/*; do ln -sfn "$(pwd)/$s" ~/.agents/skills/"$(basename "$s")"; done
```

The links point into the clone, so keep it in place; `git pull` updates the skills. To share them with a project instead, copy the skill folders into the project's `.claude/skills/` (or `.agents/skills/`). Install the four skills together: they link to each other's references.

Then ask your agent, for example, "use latex-math-writing to tighten Section 3", "use math-paper-campaign to polish this paper for submission", or "use visual-paper to build a companion site for this paper".

## Principles

- **Mathematics first.** No edit may silently change a hypothesis, conclusion, quantifier, constant, or normalisation. Prose never hides a gap.
- **Ideas before technicalities.** Explain the obstacle and the mechanism before the machinery; keep every technical condition explicit where it belongs.
- **Look at the pages.** Compiling is not checking: render the PDF and read it.
- **A figure carries an idea.** A figure or animation is made only when it adds mathematical insight or teaches; it is never decoration.
- **Nothing unchecked reaches a reader.** On a visual paper, paper text is quoted by hashed reference to the source, and every sentence an agent writes cites the source and passes an independent audit.

## Attribution and licence

These skills were adapted from a private collection developed by Scott Armstrong and Amélie Loher, and generalised for public use.

Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/); see [Licence](LICENSE).
