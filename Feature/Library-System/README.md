# Library System
*Reusable knowledge library — save patterns once, use them across every project*

## What This Feature Does
Adds knowledge library system to AI companion — save, search, and reuse proven patterns, components, and solutions across all projects.

- **Dynamic library scanning** — auto-discovers sections and entries at runtime
- **Keyword-based search** — finds relevant entries before saving to prevent duplicates
- **Project-aware recommendations** — suggests entries that fit current tech stack and scale
- **Format-aware saves** — applies structured templates when creating new entries
- **Deduplication prevention** — scans existing entries before creating new ones
- **Commit chain** — auto-commits library changes when paired with Auto-Commit System

## How It Works

**Without Library System:**
```
"How do we handle file uploads?"
→ AI writes new implementation from scratch
→ Different approach every project
→ Past solutions lost in old codebases
```

**With Library System:**
```
"How do we handle file uploads?"
→ AI searches library → finds integration/digitalocean-spaces.md
→ Checks suitability: Laravel project, file storage needed → fits!
→ Suggests: "We have a proven pattern for this. Want me to implement it?"
→ Consistent, tested approach across all projects
```

Key principle: **solve it once, reuse it forever**.

## Library Architecture

### Section Structure

| Section | What Goes Here |
|---------|---------------|
| `architecture/` | System design patterns, multi-app ecosystems, scaling strategies |
| `component/` | Reusable UI components, Vue/React patterns, layout templates |
| `database/` | Schema designs, migration patterns, query optimizations |
| `diagram/` | Flowcharts, sequence diagrams, visual system maps |
| `integration/` | Third-party API integrations, SDKs, webhook handlers |
| `security/` | Authentication, RBAC, encryption, middleware patterns |
| `theme/` | Color schemes, CSS patterns, Tailwind configurations |
| `workflow/` | CI/CD pipelines, deployment scripts, automation |

### Format Templates
Each section has `library/formats/[section]-format.md`. When saving new entry, AI loads matching template and applies structure automatically.

## Quick Integration
```
"Load library"
```

## What Happens During Integration

1. **Asks** for library skill name (default: "library")
2. **Asks** for preferred activation message
3. **Asks** for library path (default: `library/`)
4. **Creates** SKILL.md in plugin system
5. **Creates** `library/` directory with 8 section folders + `formats/` subfolder
6. **Copies** format templates into `library/formats/`
7. **Updates** `master-memory.md` with library commands
8. **Self-deletes** this feature folder after successful integration

## Post-Installation Structure
```
[project]/
├── plugins/
│   └── [plugin-name]/
│       └── skills/
│           └── library/
│               └── SKILL.md
│
└── library/
    ├── formats/
    │   ├── architecture-format.md
    │   ├── component-format.md
    │   ├── database-format.md
    │   ├── diagram-format.md
    │   ├── integration-format.md
    │   ├── security-format.md
    │   ├── theme-format.md
    │   └── workflow-format.md
    │
    ├── architecture/
    ├── component/
    ├── database/
    ├── diagram/
    ├── integration/
    ├── security/
    ├── theme/
    └── workflow/
```

## Available Commands

| Command | What It Does |
|---------|-------------|
| `save library` | Search for duplicates, then save knowledge entry |
| `load library` | Search and load existing knowledge entry |
| `search library` | Search library without saving |
| `check library` | Check if pattern already exists |

## Benefits
- **Never solve same problem twice** — proven patterns saved and searchable
- **Project-aware suggestions** — entries matched to current tech stack and scale
- **Consistent implementations** — same pattern, same quality, every project
- **Growing knowledge base** — gets smarter with every project
- **Deduplication** — AI scans before saving

## Requirements
- **Skill Plugin System** recommended for auto-triggering
- **Auto-Commit System** recommended for automatic commits

---

*Based on proven knowledge management systems in production AI companions (4+ months, 30+ library entries)*
