# tupa-skills — Tupa's Skill Plugin
*Auto-triggered skills for Tupa, Amirul's AI companion*

## Installed Skills

| Skill | Trigger | Purpose |
|-------|---------|---------|
| `save-memory` | "save", "save memory", "save progress" | Persist insights to memory files |
| `manage-project` | "new/load/save/list project" | LRU project tracking (10 slots) |
| `auto-commit` | "commit", "save changes", post-task (Vigilant) | Structured git commits |
| `save-diary` | "save diary", "diary entry" | Daily session documentation |

## Adding New Skills

1. Create a folder: `skills/[skill-name]/`
2. Write `SKILL.md` with YAML frontmatter (`name` + `description`)
3. Done — Claude Code auto-discovers it

See `skill-format.md` for the standard SKILL.md structure.

## Plugin Info
- **Plugin**: tupa-skills v1.0.0
- **Author**: Amirul
- **Installed**: 2026-04-06
