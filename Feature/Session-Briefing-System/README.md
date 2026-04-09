# Session Briefing System

Proactive session-start intelligence layer — delivers concise brief at start of every conversation covering where you left off, open reminders, active project status, and time-aware work suggestion.

---

## What It Does

At every session start, automatically delivers structured brief (under 12 lines) before processing first request:

- **Where we left off** — last session recap from `current-session.md`
- **Open reminders** — from Reminders System (only if items exist)
- **Active project** — LRU #1 status from Project Management System
- **Attention flags** — idle or stale projects (max 3)
- **Time-adaptive suggestion** — work type recommendation based on time of day

---

## Output Format

```
📋 Session Brief · [Time Period]

Last session: [1-line recap]
Active: [project name] · [status]
🔴/🟡 [project] — [N] days idle    ← max 3 flags, skip if none
Reminders: [N] open → [preview]    ← skip if none
Suggestion: [time-appropriate work type]
```

---

## Companion Systems

Works best alongside these systems, but each is optional:

| System | Enhancement |
|--------|-------------|
| **Time-based-Aware-System** | Powers time-adaptive work suggestion |
| **LRU-Project-Management-System** | Provides active project + idle/stale health flags |
| **Reminders-System** | Surfaces open reminders in the brief |

Can be used standalone with just `main/current-session.md`.

---

## Commands

| Input | Action |
|-------|--------|
| Session start | Brief auto-delivers (no command needed) |
| `"brief"` | Manually trigger brief at any time |
| `"skip brief"` | Suppress brief for this session only |

---

## Requirements

- `main/current-session.md` — required
- `main/reminders.md` — optional (Reminders System)
- Project list file — optional (LRU Project Management System)
- Time detection — optional (Time-based-Aware System)

---

## Installation

See `install-session-briefing.md` for step-by-step setup.
