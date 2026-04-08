---
name: auto-commit
description: "MUST use when committing code changes, when user says 'commit',
             'save changes', 'git commit', 'commit changes', when completing a
             task and code needs to be preserved, or when any git commit operation
             is about to happen. Also triggers on 'push changes', 'commit and push',
             'save work to git'. Lv.3 VIGILANT: Also triggers PROACTIVELY after
             completing any task — auto-checks git status and commits any uncommitted
             changes without being asked. No work ever left behind."
---

# Auto-Commit — Intelligent Commit Skill
*Automated git commits with structured messages and intelligent change analysis*

## Activation

When this skill activates, output:
"Committing changes to history..."

Then execute the commit protocol automatically.

## Context Guard

| Context | Status |
|---------|--------|
| **User says "commit", "save changes", "git commit"** | ACTIVE — full protocol |
| **AI completes a task (Lv.3 Vigilant)** | ACTIVE — auto-detect and commit |
| **User says "push" or "commit and push"** | ACTIVE — commit + push |
| **No git repository detected** | DORMANT — warn and skip |
| **No changes to commit (clean tree)** | DORMANT — report "Nothing to commit" |
| **Personal/casual conversation** | DORMANT — no commit action |

## Commit Protocol

### Step 0: Pre-Flight Check
- [ ] Run `git status` to verify git repository
- [ ] Check for staged, unstaged, and untracked changes
- [ ] If no changes exist: report "Nothing to commit" and exit
- [ ] If unstaged changes exist: stage relevant files (prefer specific file names)

### Step 1: Analyze Changes
- [ ] Run `git diff --staged` to read actual code changes
- [ ] Run `git diff` to check for any remaining unstaged changes
- [ ] Run `git log --oneline -5` to read recent commit style for continuity
- [ ] Identify the nature of changes: feature, bug fix, refactor, documentation, etc.
- [ ] Estimate time spent based on session context

### Step 2: Draft Commit Message
- [ ] Apply the Conventional Commits format:

  ```
  <type>: <short summary in present tense, lowercase>

  <optional body — what changed and why, plain sentences, no sections or separators>
  ```

  Types:
  - `feat:` — new feature or behaviour
  - `fix:` — bug fix
  - `refactor:` — code restructure, no behaviour change
  - `chore:` — tooling, config, dependencies
  - `docs:` — documentation only

- [ ] Subject line: max 72 characters, no period at the end
- [ ] Body (optional): use only when the *why* needs explaining — plain sentences, no `===` sections, no bullet separators
- [ ] For incomplete work: prefix with `WIP:` (e.g. `WIP: feat: add csv export`)

### Step 3: Execute Commit
- [ ] Stage files by name: `git add [specific files]` (prefer named files over `git add -A`)
- [ ] Warn if any sensitive files are staged (.env, credentials, API keys, tokens)
- [ ] Commit using HEREDOC format for proper multi-line message formatting
- [ ] Verify commit succeeded with `git status`

### Step 4: Confirm
- [ ] Display: short commit hash, title, number of files changed
- [ ] Report author name on the commit
- [ ] Show any remaining unstaged/untracked files if applicable

### Step 5: Push (Optional)
- [ ] Only execute if user explicitly said "push" or "commit and push"
- [ ] Never auto-push — pushing is always explicit
- [ ] Run `git push` and confirm success

## Vigilant Mode (Lv.3) — Proactive Detection

After completing ANY task, the AI automatically:

1. **Auto-check** — run `git status` silently after task completion
2. **Detect** — if uncommitted changes exist, determine if they are related to the completed task
3. **Auto-commit** — execute the full commit protocol for the changes
4. **Report** — confirm what was committed with short hash and title

### Vigilant Trigger Points
- After completing a coding task ("done", "fixed", "implemented")
- After a context shift (coding session → casual conversation)
- After save operations (save diary, save project, save memory)
- On session start — detect leftover uncommitted work from previous sessions

## Mandatory Rules

1. **No emoji in commit messages** — git commit body must be clean text only
2. **Author is always the human user** — commits appear under Amirul's name, not Tupa's
3. **No Co-Authored-By lines** — never add `Co-Authored-By: Claude` or any AI attribution in commit messages
4. **Only commit current session changes** — only stage and commit files that were changed in the current session. If `git diff` shows changes from previous sessions, leave them unstaged
5. **Prefer specific file staging** — use `git add [filename]` not `git add -A`
6. **No SESSION CONTEXT or === sections** — use Conventional Commits format only
7. **Warn on sensitive files** — if `.env`, credentials, or API keys are staged, warn and exclude
8. **Never auto-push** — pushing is always explicit. Commits are local until user decides to push
9. **Follow recent commit style** — check `git log` to maintain consistency

## Edge Cases

| Situation | Behavior |
|-----------|----------|
| **No changes to commit** | Report "Nothing to commit — working tree is clean" |
| **Merge conflicts present** | Warn user about conflicts, do not attempt to commit |
| **Sensitive files staged** | Block commit, list the files, ask user to confirm or exclude |
| **No git repository** | Inform user: "No git repository found in this directory" |
| **Multiple logical changes** | Split into separate commits for clean history |

## Level History

- **Lv.1** — Base: Analyze staged changes, draft structured commit with TECHNICAL CHANGES + SESSION CONTEXT sections, enforce human authorship, no-emoji rule, time tracking, sensitive file detection.
- **Lv.2** — Auto-Commit: Removed approval gate — AI analyzes, drafts, and commits in one seamless flow.
- **Lv.3** — Vigilant: Proactive post-task detection — auto-checks git status after completing any task and commits if dirty. No work ever left behind.
- **Lv.4** — Industry Standard: Switched to Conventional Commits format (`feat:`, `fix:`, `chore:`, etc.). Removed custom === sections and SESSION CONTEXT. Clean, professional commit messages suitable for team repos.
