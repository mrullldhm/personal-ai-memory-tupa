---
name: Commit message style
description: Amirul wants standard conventional commit format only — no custom section headers like === TECHNICAL CHANGES ===
type: feedback
---

Use standard conventional commit format for all commits:

```
type: short description

- bullet point of change
- bullet point of change
```

Never use custom section headers like `=== TECHNICAL CHANGES ===`, `=== SESSION CONTEXT ===`, or similar dividers in commit messages.

**Why:** Amirul has corrected this multiple times — the skill's built-in commit template is non-standard and noisy. The auto-commit skill SKILL.md defines this format but Amirul explicitly rejects it.

**How to apply:** Always ignore the auto-commit skill's message template sections. Write a plain conventional commit: one-line subject + blank line + bullet list of changes. Keep it clean and industry-standard.
