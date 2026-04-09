---
name: Skill folder and name field must match (lowercase-kebab)
description: SKILL.md frontmatter `name` must exactly match folder name, both lowercase-kebab. Ubuntu is case-sensitive — uppercase breaks skill loading.
type: feedback
---

Skill folder names and `name` field in SKILL.md frontmatter must be identical, lowercase-kebab only.

**Why:** Ubuntu filesystem is case-sensitive. Mismatch (e.g. folder `Work-Plan-Execution` vs name `work-plan`) breaks skill loading with error "skill name should match folder name."

**How to apply:** When creating or renaming a skill, ensure folder name = `name` field, both lowercase-kebab (e.g. `work-plan-execution`). Also ensure frontmatter exists — files with only `## Skill Name` heading will fail.
