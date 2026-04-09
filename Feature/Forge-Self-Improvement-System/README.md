# Forge Self-Improvement System
*Teach your AI to improve itself through pattern detection and skill creation*

## What This Feature Does
Adds self-improvement capability to AI companion:

- **Pattern detection** — recognizes repeated tasks handled ad-hoc 3+ times
- **Mistake prevention** — turns errors into permanent rules
- **Skill creation** — properly formatted files with trigger conditions
- **Level-up system** — skills evolve through experience (Lv.1 → Lv.2 → Lv.3+)
- **Human-in-the-loop** — AI proposes, you decide

## The Problem It Solves

Over time, patterns emerge: same request comes up repeatedly, AI makes same mistake more than once, multi-step workflow could be a single command. Without Forge, patterns go unnoticed. With Forge, AI recognizes them and proposes permanent improvements.

## Quick Integration
```bash
"Load forge"
```

## How It Works After Integration

### Automatic Detection
```
Pattern Detected: AI has formatted commit messages manually 4 times
  -> Forge proposes: "Create an auto-commit skill to handle this automatically"

Mistake Detected: AI forgot to check git status before committing (twice)
  -> Forge proposes: "Add pre-flight check to commit skill (Level-up)"

Workflow Detected: AI runs same 5-step deployment process each time
  -> Forge proposes: "Create a deploy skill to automate these steps"
```

### Manual Trigger
```
"create skill" / "new skill" / "forge this"
  -> AI analyzes recent patterns and proposes a new skill

"level up [skill name]" / "upgrade [skill name]"
  -> AI proposes improvements to existing skill

"self improve"
  -> AI reviews recent sessions for improvement opportunities
```

### The Forge Flow

```
AI detects pattern or user triggers Forge
        |
        v
AI gathers evidence (2+ concrete examples required)
        |
        v
AI proposes skill creation or level-up with full details
        |
        v
User reviews: approve / adjust / reject
        |
        v
If approved: AI creates or updates skill file
        |
        v
Skill is live and auto-triggers in future sessions
```

### Skill Level System

| Level | Meaning | Example |
|-------|---------|---------|
| **Lv.1** | Base skill | Basic commit formatting |
| **Lv.2** | Enhanced | + edge case handling |
| **Lv.3** | Proactive | + auto-detection without commands |
| **Lv.4** | Integrated | + synergy with other skills |
| **Lv.5+** | Mastered | + context-aware intelligence |

## Post-Integration Result
AI will:
- Monitor conversations for repeated patterns and improvement opportunities
- Propose new skills with proper formatting and trigger conditions
- Level-up existing skills when gaps are detected
- Always ask for approval before creating or modifying any files
- Track skill evolution through permanent level history

## Forge Principles
1. **Human-in-the-loop** — AI proposes, user approves. Always
2. **Evidence-based** — 2+ concrete examples before proposing
3. **Origin stories** — every skill traces back to a real moment
4. **Minimal viable skill** — start at Lv.1, evolve organically
5. **No over-engineering** — only forge what is genuinely needed
6. **Respect existing skills** — level-up before creating duplicates

## Synergy with Other Features

| Feature | Integration |
|---------|-------------|
| **Skill Plugin System** | Forge creates skills in plugin's folder structure |
| **Auto-Commit System** | After forging, commit the new/updated skill file |
| **Decision Log System** | Log the decision to create/level-up with rationale |
| **Save Diary System** | Document forge events in session diary |

---

*Your AI companion evolves through experience — one skill at a time*
