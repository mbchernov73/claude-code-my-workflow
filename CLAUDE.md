# CLAUDE.MD -- Academic Project Development with Claude Code

**Project:** MPidentification
**Institution:** UCLA Anderson School of Management
**Branch:** main

---

## Core Principles

- **Plan first** -- enter plan mode before non-trivial tasks; save plans to `quality_reports/plans/`
- **Verify after** -- compile/render and confirm output at the end of every task
- **Single source of truth** -- written response document is the primary artifact
- **Quality gates** -- nothing ships below 80/100
- **[LEARN] tags** -- when corrected, save `[LEARN:category] wrong → right` to MEMORY.md

---

## Folder Structure

```
MPidentification/
├── CLAUDE.MD                    # This file
├── .claude/                     # Rules, skills, agents, hooks
├── Bibliography_base.bib        # Centralized bibliography
├── Figures/                     # Figures and images
├── papers/                      # Reference papers (gitignored — large PDFs)
├── scripts/                     # Utility scripts + R code
├── quality_reports/             # Plans, session logs, merge reports
├── explorations/                # Research sandbox (see rules)
├── templates/                   # Session log, quality report templates
└── master_supporting_docs/      # Supporting documents
```

---

## Commands

```bash
# Quality score
python scripts/quality_score.py <file>

# LaTeX (if needed later — 3-pass, XeLaTeX only)
# cd Slides && TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode file.tex
# BIBINPUTS=..:$BIBINPUTS bibtex file
```

---

## Quality Thresholds

| Score | Gate | Meaning |
|-------|------|---------|
| 80 | Commit | Good enough to save |
| 90 | PR | Ready for deployment |
| 95 | Excellence | Aspirational |

---

## Skills Quick Reference

| Command | What It Does |
|---------|-------------|
| `/review-paper [file]` | Manuscript review |
| `/read-paper [file]` | In-depth paper guide |
| `/lit-review [topic]` | Literature search + synthesis |
| `/research-ideation [topic]` | Research questions + strategies |
| `/interview-me [topic]` | Interactive research interview |
| `/data-analysis [dataset]` | End-to-end R analysis |
| `/review-r [file]` | R code quality review |
| `/validate-bib` | Cross-reference citations |
| `/commit [msg]` | Stage, commit, PR, merge |
| `/learn [skill-name]` | Extract discovery into persistent skill |
| `/context-status` | Show session health + context usage |
| `/deep-audit` | Repository-wide consistency audit |
| `/proofread [file]` | Grammar/typo review |
| `/compile-latex [file]` | 3-pass XeLaTeX + bibtex (if slides needed) |
| `/deploy [LectureN]` | Render Quarto + sync to docs/ (if slides needed) |

---

## Slides / Quarto

No Beamer slides or Quarto decks for this project -- written response only.
Will activate slide-related workflows if/when presentation materials are needed.

---

## Current Project State

| Component | File(s) | Status | Description |
|-----------|---------|--------|-------------|
| BCZZ (2022) | `papers/` | Reference | "Monetary Policy Risk: Rules vs Discretion" (RFS) |
| CK (2026) | `papers/` | Under review | Cieslak & Khorrami critique of BCZZ identification |
| Response | TBD | In progress | Counter-arguments to CK critique |
| Bibliography | `Bibliography_base.bib` | Active | Project references |
