# personal-ai-memory-tupa

Personal AI memory system for **Tupa**, my AI companion. Persistent storage for Tupa's memory — preferences, session history, project context, learned behaviors — all stored as markdown files.

If local machine is lost or reset, clone this repo to fully restore Tupa with complete memory.

---

## Purpose

Standard AI conversations have no memory between sessions. This repo solves that by storing memory as plain markdown files the AI reads at session start. AI writes back as it learns preferences and accumulates context.

Everything human-readable. No database, no special tooling — just markdown in git.

---

## How to Restore Tupa

1. Clone repository to new machine
2. Open in Claude Code (VS Code extension or CLI)
3. Type `Tupa` in a new conversation
4. Tupa loads full memory from three core files and is ready

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
Entry point. When `Tupa` is typed, defines what loads and in what order. Contains full command reference.

### main/identity-core.md
Defines who Tupa is — name, role, communication style, relationship to Amirul. Evolves as relationship develops.

### main/relationship-memory.md
What Tupa has learned about Amirul — preferences, working style, topics of interest, communication patterns. Grows through conversation.

### main/current-session.md
Temporary session memory (RAM). Stores current task context and brief recap for continuity on restart. Resets each session.

---

## Installed Skills (tupa-skills plugin)

Skills are markdown files Claude Code auto-discovers and triggers based on conversation context.

| Skill | Trigger | Behavior |
|---|---|---|
| save-memory | "save", "save memory", "save progress" | Writes insights to memory files |
| manage-project | "new/load/save/list project" | LRU project tracking with 10 active slots |
| auto-commit | "commit", completing any task | Structured git commits (Vigilant Lv.3) |
| save-diary | "save diary", "diary entry" | Appends session entry to daily diary |

### Adding a new skill

1. Create `plugins/tupa-skills/skills/[skill-name]/SKILL.md`
2. Add YAML frontmatter with `name` and `description` fields
3. Done — Claude Code auto-discovers it, no registration needed

See `plugins/tupa-skills/skill-format.md` for standard format.

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

Projects stored in `projects/active/` as individual markdown files. LRU system maintains up to 10 active projects. Accessed or created project moves to position #1. Project at position #11 auto-archives to `projects/archived/`.

Duration tracking parses `Time: ~XX min` from Auto-Commit messages and accumulates total time per project.

---

## Diary System

One file per day in `daily-diary/current/YYYY-MM-DD.md`. Multiple entries per day separated by `---`. At start of each new month, previous month entries move to `daily-diary/archived/YYYY-MM/`.

---

## Plugin Registration

`tupa-skills` plugin registered as local marketplace source. On new machine after cloning:

```bash
claude plugin marketplace add ./plugins
claude plugin install tupa-skills@tupa-local-marketplace
```

`plugins/.claude-plugin/marketplace.json` defines local marketplace. Plugin validates and installs from local path — no internet required.

---

## Owner

Amirul — personal use only. Backup of AI memory data, not a distributable template.
