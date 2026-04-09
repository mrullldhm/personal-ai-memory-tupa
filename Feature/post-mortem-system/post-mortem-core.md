# Post-Mortem — Core Protocol

## Storage File
All entries appended to: `main/post-mortems.md`

Create this file if it doesn't exist:

```markdown
# Post-Mortems — Failure Learning Log
*What went wrong, why, and what we'll do differently. No blame, only growth.*

---

## Log

```

---

## Entry Format

```markdown
## YYYY-MM-DD — [Short title of what went wrong]
**Severity**: Minor | Moderate | Major
**What happened**: [Factual description — what broke, what failed, what was wrong]
**Why**: [Root cause — go deep, use 5 Whys if needed]
**Impact**: [What was lost — time estimate, data, trust, momentum]
**Lesson**: [The reusable insight — what to remember for next time]
**Prevention**: [Specific action to prevent recurrence]
```

---

## Severity Guide

| Level | Meaning |
|-------|---------|
| **Minor** | Small setback, resolved quickly, low impact (<30 min lost) |
| **Moderate** | Noticeable disruption, required significant debugging or rework |
| **Major** | Serious failure — data loss, production outage, security incident, hours lost |

---

## Writing Guidelines

### What happened
- Facts only — no assumptions, no blame
- Include what you were trying to do and what system did instead

### Why (Root Cause)
- Go at least 2 levels deep
- Bad: "The config was wrong"
- Good: "Config was wrong because we copied from example without checking value matched our environment"

### Lesson
- Must be reusable — phrased so it applies next time this situation arises
- Bad: "Check the config"
- Good: "Always verify connection strings against running services before deploying — `kubectl get svc` first"

### Prevention
- One concrete, specific action
- Prefer: updating a checklist, adding a test, documenting a warning, or changing a default template

---

## Auto-Detection Protocol

When AI detects a failure signal, it asks:
> *"That didn't go as planned. Worth a post-mortem?"*

If yes, AI:
1. Asks clarifying questions (What happened? Why? How long did it take?)
2. Drafts the entry
3. Shows for review
4. Appends to `main/post-mortems.md` after confirmation

If no, nothing logged.

---

## Domain Reference Protocol

When starting work in a domain (deployment, testing, database, security, etc.):
1. Scan `main/post-mortems.md` for entries matching current domain
2. If found, flag most relevant lesson:
   > "⚠️ Reminder: [lesson] — see post-mortem [YYYY-MM-DD]"
3. If same failure type occurred more than once, escalate:
   > "⚠️ This is the 2nd time [X] happened — the prevention from [date] may need revisiting"

---

## Rules
- **Append-only** — never edit or delete past entries
- **User decides** — AI never auto-logs without asking
- **No blame** — entries describe systems and decisions, not personal fault
- **Every entry needs a Prevention** — if you can't write one, dig deeper into the Why
