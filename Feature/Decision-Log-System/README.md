# Decision Log System
*Append-only record of non-obvious decisions your AI companion helps you make*

## What This Feature Does
Dedicated decision log that captures reasoning behind important choices:

- **Append-only log** of architectural, technical, and strategic decisions
- **Context + Decision + Rationale** format per entry
- **Searchable history** of "why did we do it this way?"
- **Never edited** — past decisions immutable, new context creates new entries
- **Cross-session persistence** — survives memory resets and context changes

## The Problem It Solves

You and AI make dozens of decisions during a project:
- "Should we use approach A or B?"
- "Why did we structure it this way?"
- "What was the trade-off we accepted?"

Without a log, these decisions exist only in conversation history — compacted, archived, or lost. The Decision Log captures the WHY behind non-obvious choices, creating an immutable record future sessions can reference.

## Quick Integration
```bash
"Load decision-log"
```

## How It Works After Integration

### Decision Entry Format
```markdown
## YYYY-MM-DD -- Short title of the decision
**Context**: What situation prompted this decision
**Decision**: What was chosen and what was rejected
**Rationale**: Why this choice was made (trade-offs, constraints, evidence)
```

### Example Entries
```markdown
## 2025-10-01 -- Database: PostgreSQL over MongoDB
**Context**: Starting new project, need database. Data is relational with many foreign key relationships.
**Decision**: PostgreSQL with Prisma ORM. Rejected MongoDB (document model doesn't fit relational data), rejected raw SQL (maintenance burden).
**Rationale**: Prisma provides type-safe queries and migration management. PostgreSQL handles relational model naturally. Team has more SQL experience than NoSQL. Trade-off: less flexible schema evolution, accepted because data model is well-defined.

## 2025-10-03 -- Auth: session-based over JWT
**Context**: Need authentication for web app. Considering JWT tokens vs server-side sessions.
**Decision**: Server-side sessions with Redis store. Rejected JWT (can't revoke tokens without blacklist, which re-introduces server state anyway).
**Rationale**: App requires immediate session revocation (admin can deactivate users). JWT's stateless advantage disappears when you need a blacklist. Sessions in Redis give revocation + horizontal scaling.
```

### When to Log a Decision
AI automatically detects decision-worthy moments:
- "Let's go with X instead of Y"
- "We chose this because..."
- "The trade-off is..."
- "Should we use A or B?" (after decision made)
- Architecture changes, technology choices, workflow decisions
- Anything where future-you would wonder "why?"

### What NOT to Log
- Obvious choices (using git for version control)
- Temporary decisions (formatting preferences that can change anytime)
- Implementation details (how, not why)

## Why Append-Only?

1. **Immutability** — past decisions reflect past context. Editing rewrites history.
2. **Audit trail** — see how thinking evolved over time.
3. **Contradiction is fine** — if you reverse a decision, log a NEW entry explaining why. Both entries stay.
4. **Searchable** — grep for keywords to find when and why a decision was made.

## Post-Integration Structure
```
main/
├── identity-core.md          # Existing
├── relationship-memory.md    # Existing
├── current-session.md        # Existing
└── decisions.md              # NEW: append-only decision log
```

## Synergy with Other Features

| Feature | Synergy |
|---------|---------|
| **Echo Memory Recall** | Search decision log with "do you remember why we chose X?" |
| **Save Diary System** | Diary captures what happened; decision log captures why |
| **Auto-Commit System** | Decision log entries can trigger a commit |
| **Reminders System** | "Revisit this decision in 2 weeks" becomes a reminder |

---

*Capture the WHY behind every important choice — future you will thank present you*
