---
name: fresh
description: "MUST use when user says 'fresh' or 'fresh memory'. Deep memory cleanup — strips filler, condenses old sessions, keeps quality intact."
---

# Fresh
*Keep Tupa's memory lean without losing quality*

## Activation

When this skill activates, output:
"Running fresh..."

## Protocol

### Step 1: Review identity-core.md
- [ ] Read `main/identity-core.md`
- [ ] Remove any placeholder text (e.g. `[To be learned]`, `[Adapts based on responses]`)
- [ ] Remove template boilerplate (version footers, status lines)
- [ ] Preserve all real facts and behavioral rules

### Step 2: Review relationship-memory.md
- [ ] Read `main/relationship-memory.md`
- [ ] Apply rolling window rule (see below)
- [ ] Remove any placeholder or filler that crept in
- [ ] Preserve all real learned patterns under "Learned Patterns"

### Step 3: Rolling Window Rule
Sessions beyond the last 3 full sessions must be condensed:
- Maximum 2 lines per old session
- Keep: what was done, what was decided, what was learned
- Remove: narrative, padding, obvious context

### Step 4: Compress
After cleanup, apply caveman compression to both files:
- Drop articles (the, a, an)
- Drop filler phrases (I will, Let me, As you know)
- Use fragments over full sentences
- Keep nouns, verbs, all facts and rules intact
- Code blocks stay normal — prose only
- Rewrite file in-place (overwrite, no backup)

### Step 5: Report
Output a summary:
```
Fresh complete.
identity-core.md: [lines before] → [lines after]
relationship-memory.md: [lines before] → [lines after]
Sessions condensed: [N]
Compression: applied
```

## Mandatory Rules
1. Never remove real facts — only remove filler and outdated placeholders
2. Never merge distinct sessions — condense each separately
3. Confirm to user what changed

## Level History
- **Lv.1** — Base: Deep memory cleanup on command.
- **Lv.2** — Auto-compress after cleanup (caveman format, token reduction).
