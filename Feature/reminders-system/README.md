# Reminders System
*Persistent cross-session reminders that survive memory resets*

## What This Feature Does
Dedicated reminders file that persists independently from session memory:

- **Persistent reminders** that survive session resets and context changes
- **Open/Completed lifecycle** for tracking active and resolved items
- **Deadline awareness** for time-sensitive tasks
- **Session-end auto-check** ensures reminders reviewed before closing
- **Separate from session RAM** — reminders never get overwritten

## The Problem It Solves

Session memory (`current-session.md`) resets every session. If you tell AI "remind me to check the deployment tomorrow", that reminder is lost when session ends. Reminders System creates a dedicated file AI checks at session start and updates at end.

## Quick Integration
```bash
"Load reminders"
```

## How It Works After Integration

### Reminder Lifecycle
```
User mentions follow-up / pending task / deadline
        |
        v
AI adds to reminders.md -> Open section
        |
        v
Each session start: AI reads reminders, flags urgent items
        |
        v
When resolved: AI moves to Completed section with date
```

### Reminder Format
```markdown
## Open
- **Deploy verification**: Check production deployment is healthy after Friday release
- **API key rotation** (by 2025-10-15): Rotate staging API keys before security audit
- **Follow up with team**: Ask about database migration timeline

## Completed
- **Unit test coverage** (completed 2025-10-01): Added tests for auth module, coverage now 85%
- **Dependency update** (completed 2025-09-28): Updated framework to v3.2, all tests passing
```

### Natural Language Triggers
AI automatically detects reminder-worthy phrases:
- "remind me to..." / "don't let me forget..."
- "we need to follow up on..."
- "next session, we should..."
- "by [date], make sure..."
- "check on this later"

### Session Integration
- **Session start**: AI reads `reminders.md`, mentions urgent or overdue items
- **Session end**: AI reviews Open reminders, moves completed ones, adds new ones
- **Deadline tracking**: Reminders with dates flagged when approaching or overdue

## Why Separate from Session Memory?

| Feature | Session Memory | Reminders |
|---------|---------------|-----------|
| **Persistence** | Resets each session | Survives indefinitely |
| **Purpose** | Current conversation context | Cross-session follow-ups |
| **Update pattern** | Overwritten each session | Append + move lifecycle |
| **Checked** | Loaded at session start | Loaded AND reviewed at session start |
| **Size** | Stays small (RAM-like) | Grows over time |

## Post-Integration Structure
```
main/
├── identity-core.md          # Existing
├── relationship-memory.md    # Existing
├── current-session.md        # Existing
└── reminders.md              # NEW: persistent reminders
```

## Benefits
- **Nothing gets lost** between sessions
- **Deadline awareness** prevents missed commitments
- **Zero extra effort** — AI detects and manages reminders naturally
- **Searchable history** of completed reminders
- **Independent persistence** — survives session resets, context switches, memory consolidation

---

*Add persistent memory to AI companion — never lose a follow-up again*
