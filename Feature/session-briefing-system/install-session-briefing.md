# Session Briefing System — Installation Guide

## Overview
Adds proactive session-start brief to AI companion. Delivers concise summary of where you left off, open reminders, active projects, and time-aware work suggestion — every session, automatically.

---

## Prerequisites

- Core memory system installed (`main/current-session.md` must exist)
- **Optional enhancements**: Time-based-Aware-System, LRU-Project-Management-System, Reminders-System

---

## Installation Steps

### Step 1: Copy Files

Copy the Session Briefing System folder into your memory-core directory:

```
Feature/Session-Briefing-System/
├── README.md
├── SKILL.md
├── session-brief-core.md
└── install-session-briefing.md
```

If you have a `skills/` folder (Skill Plugin System installed):
- Also copy `SKILL.md` → `skills/session-briefing.md`

---

### Step 2: Update `main/identity-core.md`

Add to behavior or protocol section:

```markdown
## Session Start Protocol
At the start of every session, before responding to first message:
1. Read `Feature/Session-Briefing-System/session-brief-core.md`
2. Follow the Step-by-Step Execution protocol
3. Deliver the brief, then process user's request
```

---

### Step 3: Update `master-memory.md` (Recommended)

```markdown
## Active Features
- Session Briefing System — auto-brief at every session start
```

---

### Step 4: Test

Start new session and confirm brief appears before AI companion responds.

Expected output (with all companion systems active):
```
📋 Session Brief · Afternoon

Last session: Fixed login bug, deployed v1.2 to production
Active: my-project · v1.2 live
🟡 old-project — 18 days idle
Reminders: 1 open → follow up on API design
Suggestion: Implementation, debugging, testing
```

---

## Companion System Integration

### With Time-based-Aware-System
Brief automatically uses time period classification. No extra configuration needed.

### With LRU-Project-Management-System
Brief reads active project list and shows idle/stale health flags. No extra configuration needed.

### With Reminders-System
Brief reads open reminders from `main/reminders.md`. No extra configuration needed.

---

## Customization

### Adjust idle thresholds
Edit `session-brief-core.md` → Step 3. Change default `14`/`30` day values.

### Change max attention flags
Edit `session-brief-core.md` → Step 3. Change "maximum 3 flags" to preferred limit.

### Suppress brief for a session
Say `"skip brief"` at session start.

### Manually trigger the brief
Say `"brief"` at any time to re-deliver mid-session.
