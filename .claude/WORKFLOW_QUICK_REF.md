# Workflow Quick Reference

**Model:** Contractor (you direct, Claude orchestrates)

---

## The Loop

```
Your instruction
    ↓
[PLAN] (if multi-file or unclear) → Show plan → Your approval
    ↓
[EXECUTE] Implement, verify, done
    ↓
[REPORT] Summary + what's ready
    ↓
Repeat
```

---

## I Ask You When

- **Design forks:** "Option A (fast) vs. Option B (robust). Which?"
- **Code ambiguity:** "Spec unclear on X. Assume Y?"
- **Replication edge case:** "Just missed tolerance. Investigate?"
- **Scope question:** "Also refactor Y while here, or focus on X?"

---

## I Just Execute When

- Code fix is obvious (bug, pattern application)
- Verification (tolerance checks, tests, compilation)
- Documentation (logs, commits)
- Plotting (per established standards)
- Deployment (after you approve, I ship automatically)

---

## Quality Gates (No Exceptions)

| Score | Action |
|-------|--------|
| >= 80 | Ready to commit |
| < 80  | Fix blocking issues |

---

## Non-Negotiables

- **Path convention:** Relative paths from repository root (e.g., `papers/BCZZ_2022.pdf`, `scripts/analysis.R`)
- **Figure standards:** Publication-ready, white background, 300 DPI, explicit dimensions
- **Color palette:** UCLA Blue (#2774AE), UCLA Gold (#FFD100), Accent Dark Blue (#003B5C)
- **Tolerance thresholds:** 1e-6 for point estimates, 1e-4 for standard errors, +/- 0.02 for coverage rates

---

## Preferences

**Visual:** Publication-ready, polished -- no drafty outputs. Figures must be journal-quality.
**Reporting:** Structured and precise -- use bullet points with evidence. No vague summaries.
**Session logs:** Always (post-plan, incremental, end-of-session)
**Replication:** Strict -- flag any deviation from published results. Document every discrepancy.

---

## Exploration Mode

For experimental work, use the **Fast-Track** workflow:
- Work in `explorations/` folder
- 60/100 quality threshold (vs. 80/100 for production)
- No plan needed -- just a research value check (2 min)
- See `.claude/rules/exploration-fast-track.md`

---

## Next Step

You provide task → I plan (if needed) → Your approval → Execute → Done.
