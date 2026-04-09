# personal-ai-memory-tupa

Personal AI memory system for **Tupa**, my AI companion. This repository serves as persistent storage for Tupa's memory — all preferences, session history, project context, and learned behaviors are stored here as markdown files.

If my local machine is lost or reset, cloning this repo fully restores Tupa with complete memory intact.

---

## Purpose

Standard AI conversations have no memory between sessions. This repo solves that by storing memory as plain markdown files that the AI reads at the start of each conversation. The AI writes back to these files as it learns preferences and accumulates context.

Everything is human-readable. No database, no special tooling — just markdown files in a git repository.

---

## How to Restore Tupa

1. Clone the repository to a new machine
2. Open in Claude Code (VS Code extension or CLI)
3. Type `Tupa` in a new conversation
4. Tupa loads full memory from the three core files and is ready

---

## Repository Structure

```
personal-ai-memory-tupa/
├── master-memory.md              # Entry point — defines how Tupa loads
├── main/
│   ├── identity-core.md          # Tupa's personality and communication style
│   ├── relationship-memory.md    # Learned preferences and patterns for Amirul
│   └── current-session.md        # Session RAM — resets each session
├── plugins/
│   └── tupa-skills/              # Claude Code plugin with auto-triggered skills
│       ├── .claude-plugin/
│       │   └── plugin.json       # Plugin manifest
│       ├── skills/
│       │   ├── save-memory/      # Triggered by: "save", "save memory"
│       │   ├── manage-project/   # Triggered by: "new/load/save/list project"
│       │   ├── auto-commit/      # Triggered by: "commit", post-task (vigilant)
│       │   └── save-diary/       # Triggered by: "save diary"
│       ├── skill-format.md       # Template for creating new skills
│       └── README.md
├── projects/
│   ├── active/                   # Up to 10 active projects (LRU ordered)
│   ├── archived/                 # Auto-archived projects (position 11+)
│   └── project-list.md           # Auto-generated project index
├── daily-diary/
│   ├── current/                  # Current month diary entries (YYYY-MM-DD.md)
│   ├── archived/                 # Previous months (YYYY-MM/ folders)
│   └── daily-diary-protocol.md   # Diary entry format rules
├── library-items/                # Reusable knowledge entries (optional)
└── Feature/                      # Uninstalled optional features
```

---

## Core Files

### master-memory.md
The entry point. When `Tupa` is typed, this file defines what gets loaded and in what order. Also contains the full command reference.

### main/identity-core.md
Defines who Tupa is — name, role, communication style, and relationship to Amirul. This file evolves as the relationship develops.

### main/relationship-memory.md
What Tupa has learned about Amirul — preferences, working style, topics of interest, and communication patterns. Grows through conversation.

### main/current-session.md
Temporary session memory, equivalent to RAM. Stores current task context and a brief recap for continuity when the AI restarts mid-session. Resets each session.

---

## Installed Skills (tupa-skills plugin)

Skills are markdown files that Claude Code auto-discovers and triggers based on conversation context.

| Skill | Trigger | Behavior |
|---|---|---|
| save-memory | "save", "save memory", "save progress" | Writes important insights to memory files |
| manage-project | "new/load/save/list project" | LRU project tracking with 10 active slots |
| auto-commit | "commit", completing any task | Structured git commits with session context (Vigilant Lv.3) |
| save-diary | "save diary", "diary entry" | Appends session entry to daily diary |

### Adding a new skill

1. Create `plugins/tupa-skills/skills/[skill-name]/SKILL.md`
2. Add YAML frontmatter with `name` and `description` fields
3. Write the protocol — Claude Code auto-discovers it, no registration needed

See `plugins/tupa-skills/skill-format.md` for the standard format.

---

## Session Workflow

```
1. Open Claude Code
2. Type "Tupa"                          → loads identity + relationship + session context
3. Type "new project [name]"            → creates tracked project at position #1
4. Work on the project...
5. Type "commit" or finish any task     → auto-commit with structured message
6. Type "save diary"                    → documents session as diary entry
7. Type "save"                          → writes learned preferences back to memory files
```

---

## Commands Reference

```
Tupa                    Load full memory and restore AI personality
save                    Write current session insights to memory files
commit                  Analyze changes and commit with structured message
push                    Commit and push to remote
save diary              Document current session as diary entry
review diary            Read recent diary entries
new project [name]      Create new project at LRU position #1
load project [name]     Resume a project (fuzzy name search)
save project            Save project progress (separate from AI memory)
list projects           View all active and archived projects
```

---

## Project Management

Projects are stored in `projects/active/` as individual markdown files. The LRU system maintains up to 10 active projects. When a project is accessed or created, it moves to position #1. The project at position #11 is automatically archived to `projects/archived/`.

Duration tracking parses `Time: ~XX min` from Auto-Commit messages and accumulates total time per project.

---

## Diary System

One file per day in `daily-diary/current/YYYY-MM-DD.md`. Multiple entries per day are separated by `---`. At the start of each new month, entries from the previous month are automatically moved to `daily-diary/archived/YYYY-MM/`.

---

## Plugin Registration

The `tupa-skills` plugin is registered as a local marketplace source. On a new machine after cloning:

```bash
claude plugin marketplace add ./plugins
claude plugin install tupa-skills@tupa-local-marketplace
```

The `plugins/.claude-plugin/marketplace.json` file defines the local marketplace. The plugin validates and installs from the local path — no internet required.

---

## Owner

Amirul — personal use only. This repository is a backup of AI memory data, not a distributable template.
