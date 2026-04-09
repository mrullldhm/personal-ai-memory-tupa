# Post-Mortem System — Installation Guide

## Overview
Adds failure learning log to AI companion. AI auto-detects failure signals, asks whether to log them, and references past lessons when working in same domain.

---

## Prerequisites

- Core memory system installed (`main/` folder must exist)
- No other systems required — fully standalone

---

## Installation Steps

### Step 1: Copy Files

Copy the Post-Mortem System folder into your memory-core directory:

```
Feature/Post-Mortem-System/
├── README.md
├── SKILL.md
├── post-mortem-core.md
└── install-post-mortem.md
```

If you have a `skills/` folder (Skill Plugin System installed):
- Also copy `SKILL.md` → `skills/post-mortem.md`

---

### Step 2: Create the Log File

Create `main/post-mortems.md`:

```markdown
# Post-Mortems — Failure Learning Log
*What went wrong, why, and what we'll do differently. No blame, only growth.*

---

## Log

*(No entries yet)*
```

---

### Step 3: Update `main/identity-core.md`

Add to behavior or protocol section:

```markdown
## Post-Mortem Protocol
When a failure signal is detected (deployment failure, broken tests, wasted time, architecture reversal, security incident, data loss):
1. Ask: "That didn't go as planned. Worth a post-mortem?"
2. If yes: follow `Feature/Post-Mortem-System/post-mortem-core.md`
3. Append entry to `main/post-mortems.md`
4. When starting work in a domain, check `main/post-mortems.md` for relevant lessons
```

---

### Step 4: Update `master-memory.md` (Recommended)

```markdown
## Active Features
- Post-Mortem System — failure learning log, auto-detected
```

---

### Step 5: Test

Simulate failure scenario (e.g., "my deployment just failed") and verify AI asks whether to log a post-mortem.

---

## Companion System Integration

### With Session Briefing System
Flags recent post-mortems at session start when working in relevant domain. No extra configuration needed.

### With Decision-Log-System
- **Decision Log**: records *what you chose* and *why*
- **Post-Mortem Log**: records *what went wrong* and *what to do differently*

Both append-only — consider linking related entries by date.

### With Save-Diary-System
Major severity post-mortems are good diary entry candidates. Log post-mortem first, then save diary entry referencing it.

---

## Customization

### Add more auto-detection signals
Edit `SKILL.md` → Auto-Detection Triggers table.

### Change log file location
Default: `main/post-mortems.md`. To change, update path in `post-mortem-core.md` and `identity-core.md`.

### Disable auto-detection
Remove auto-detection block from `identity-core.md`. Manual trigger (`"post-mortem"`) still works.
