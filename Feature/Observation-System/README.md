# Observation System
*Tiered code awareness — see clearly before you act*

## What This Feature Does

Adds 4-tier observation system to AI companion — structured project inspection at different depths.

- **Survey** (Lv.1) — Quick bird's-eye view of project health (~30 sec)
- **Investigate** (Lv.2) — Deep dive into specific area, bug, or file (~5 min)
- **Refine** (Lv.2) — Review and fix changed code for quality (~5 min)
- **Audit** (Lv.3) — Full system audit with architecture mapping (~15 min)

## Why Tiered Observation?

```
"How's the project?"     → Survey    (30 sec, one screen)
"What's going on here?"  → Investigate (5 min, focused)
"Clean up my code"       → Refine    (5 min, corrective)
"Show me everything"     → Audit     (15 min, exhaustive)
```

**Right depth for right question.** Don't audit when you need survey. Don't survey when you need audit.

## Key Innovation: Corrective vs Investigative

Three tiers are **investigative** — observe and report:
- Survey, Investigate, Audit → "Here's what I found"

One tier is **corrective** — observes AND fixes:
- Refine → "Here's what I found, and here's the fix (with your permission)"

Refine is the quality gate you run before every commit.

## Escalation Pattern

```
Survey spots problem    →  Investigate that area
Investigate finds depth →  Audit the full system
Any tier finds code     →  Refine specific files
Refine finds systemic   →  Audit the full system
```

## Cross-Feature Integration

| Feature | Integration |
|---------|------------|
| **Library System** | Link findings to knowledge entries; suggest new entries for undocumented patterns |
| **Post-Mortem System** | Cross-reference project against past incidents during Survey |
| **Work-Plan Execution** | Survey before planning; Refine after each task; Audit at milestones |
| **Auto-Commit System** | Refine → fix → auto-commit chain |

All integrations optional — Observation System works independently.

## Cost Awareness

| Tier | Effort | Delegation | Why |
|------|--------|-----------|-----|
| **Survey** | Low | Can delegate to lighter model/agent | Mostly file scanning, git status |
| **Investigate** | Medium | Primary AI recommended | Code comprehension, flow tracing |
| **Refine** | Medium | Primary AI recommended | Must understand intent before fixing |
| **Audit** | High | Primary AI recommended | Cross-system analysis, risk assessment |

**Cost-saving pattern**: frequent cheap observation prevents expensive deep audits. Survey daily, Refine before every commit, Audit at milestones.

## Quick Start

```
"survey"                        → Quick project health check
"investigate authentication"    → Deep dive into auth system
"investigate bug login fails"   → Trace bug to root cause
"refine"                        → Review all changed files
"refine src/services/Auth.cs"   → Review specific file
"audit"                         → Full system audit
"audit cross"                   → Cross-project comparison
```

---

*Observation System v1.0*
