# Work — Plan Execution System
*From plan mode to tracked execution — every step committed, every reset survivable*

## What This Feature Does
Adds plan execution lifecycle to AI companion — captures plans into trackable files, executes each task with checkpoint commits, and resumes after any context reset.

- **Plan capture** — copies plan mode output into trackable `project-plan.md` with checkbox format
- **Checkbox execution** — converts plan steps into executable `[ ]` todos grouped by phase
- **Progress tracking** — completed tasks marked `[x]`, blocked tasks marked `[~]`
- **Per-task commit discipline** — chains with Auto-Commit to commit after each completed todo
- **Resume capability** — survives context resets by reading plan file and picking up at next `[ ]`
- **Plan rotation** — archives when plan file exceeds 1,000 lines

## How It Works

The plan file IS the recovery mechanism. When context resets, AI reads the file and picks up exactly where it left off.

### Example: A Work Session

**Starting a plan:**
```
You: "copy plan"
→ AI scans for latest plan file from plan mode
→ Converts plan steps to checkboxes, preserves diagrams
→ Writes to Project Resources/project-plan.md
→ Begins executing:
  Task 1 done → Auto-Commit fires → [x] marked
  Task 2 done → Auto-Commit fires → [x] marked
  Task 3 done → Auto-Commit fires → [x] marked...
```

**After a context reset:**
```
You: "resume plan"
→ AI reads project-plan.md
→ Reports: "7 of 12 items done. Next: implement user authentication"
→ Continues executing from exactly where it left off
```

## Plan Architecture

### File Format
```markdown
# Project Plan - MyApp
Created: 2026-02-27

## Architecture
[Preserved diagrams from original plan]

## Implementation Plan

### Phase 1: Database Setup
- [x] Create user migration
- [x] Create product migration
- [ ] Add seed data

### Phase 2: API Endpoints
- [ ] User CRUD endpoints
- [~] Payment integration (blocked: waiting for API keys)
```

### Progress States

| Symbol | Meaning | What Happens |
|--------|---------|-------------|
| `[ ]` | Pending | Not yet started — next in queue |
| `[x]` | Completed | Done and committed |
| `[~]` | Blocked | Flagged, skipped — AI continues to next |

### The Execution Loop
```
For each [ ] todo item:
  1. Execute the task (write code, create files)
  2. Auto-Commit fires (if installed) → structured commit
  3. Mark [x] in the plan file
  4. Checkpoint save every 5 items
  5. Move to next [ ] item
```

### Resume After Reset
```
1. User says "resume plan"
2. AI reads project-plan.md
3. Counts completed [x] vs pending [ ] items
4. Reads Architecture section for technical context
5. Continues from next [ ] item
```

## Quick Integration
```
"Load work-plan"
```

## What Happens During Integration

1. **Asks** for plan skill name (default: "work-plan")
2. **Asks** for plan storage location (default: "Project Resources")
3. **Asks** for plan source path
4. **Asks** for plan file line limit (default: 1000 lines)
5. **Creates** SKILL.md in plugin system
6. **Creates** `plan-format.md` in plan location folder
7. **Updates** `master-memory.md` with plan execution commands
8. **Self-deletes** this feature folder after successful integration

## Available Commands

| Command | What It Does |
|---------|-------------|
| `copy plan` | Copy latest plan into execution format (fresh start) |
| `append plan` | Add new plan steps to existing plan |
| `resume plan` | Resume execution after context reset |

## Benefits
- **Never lose plan progress** — every completed task committed or checkpointed
- **Survives context resets** — resume from exactly right task after any interruption
- **Complete execution history** — git log shows plan progression commit by commit
- **Scales to large plans** — automatic line-limit rotation keeps files manageable
- **Works independently** — no other features required (but pairs perfectly with Auto-Commit)

## Synergy: Works Best With Auto-Commit
When both installed, Work automatically chains — each completed todo triggers a structured commit. Git history maps directly to your project plan.

## Requirements
- Core memory system installed
- **Skill Plugin System** recommended for auto-triggering
- **Auto-Commit System** optional but recommended

---

*Based on proven plan execution systems in production AI companions*
