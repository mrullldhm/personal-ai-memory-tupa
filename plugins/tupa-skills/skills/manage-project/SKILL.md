---
name: manage-project
description: "Auto-triggers on 'new project [name]', 'load project [name]',
             'save project', 'list projects'. Also triggers on 'create project',
             'resume project', 'open project', 'show projects', or when user
             mentions switching between active projects."
---

# Manage Project -- LRU Project Management Skill
*Smart project tracking with automatic memory management.*

## Activation

When this skill activates, silently determine which command was triggered and execute the matching protocol section.

## Context Guard

| Context | Status |
|---------|--------|
| **User says "new project [name]"** | ACTIVE -- create project |
| **User says "load project [name]"** | ACTIVE -- load and resume |
| **User says "save project"** | ACTIVE -- save current progress |
| **User says "list projects"** | ACTIVE -- display all projects |
| **Mid-conversation (no project command)** | DORMANT |

---

## Protocol: New Project

**Trigger**: `"new project [name]"` or `"create project [name]"`

### Step 1: Parse Command
- [ ] Extract project name from command
- [ ] Check if project name already exists in active or archived
- [ ] If exists: suggest loading instead, or ask for a different name

### Step 2: Gather Project Details
- [ ] Ask user for brief description (1-2 sentences)
- [ ] Get current date using platform-appropriate time command
- [ ] Note any initial requirements, goals, or tech stack

### Step 3: Create Project File
- [ ] Generate project file from **Embedded Project Template** (see below)
- [ ] Fill in: name, description, created date, status (Active)
- [ ] Save to `projects/active/[name].md`

### Step 4: Apply LRU Positioning
- [ ] Insert new project at position #1
- [ ] Shift all existing active projects down by 1
- [ ] If position #11 exists after shift:
  - Move to `projects/archived/`
  - Update status to "Archived (LRU)"
  - Add archive date

### Step 5: Update Project List
- [ ] Regenerate `projects/project-list.md`
- [ ] New project at top of active section

### Step 6: Update Session Memory
- [ ] Add to current-session.md:
  ```
  ## Active Project
  - Name: [project name]
  - Started: [date/time]
  - Context: [description]
  ```

### Step 7: Confirm
- [ ] Display confirmation with project name, position #1, and description

---

## Protocol: Load Project

**Trigger**: `"load project [name]"` or `"resume project [name]"`

### Step 1: Search for Project
- [ ] Parse project name from command
- [ ] Search `projects/active/` first, then `projects/archived/`
- [ ] Use fuzzy matching if exact name not found (partial names, case-insensitive)

### Step 2: Handle Search Results
- [ ] If multiple matches: show list, ask for selection
- [ ] If not found: suggest similar projects, offer to create new

### Step 3: Load Project Data
- [ ] Read project file completely
- [ ] Extract: description, last accessed, status, recent sessions, duration

### Step 4: Apply LRU Positioning
- [ ] Move project to position #1, shift others down
- [ ] If position #11 exists: auto-archive

### Step 5: Update Project File
- [ ] Update "Last Accessed" to current date/time

### Step 6: Update Project List
- [ ] Regenerate `projects/project-list.md`

### Step 7: Load into Session Memory
- [ ] Update `main/current-session.md` with active project context

### Step 8: Display Summary
- [ ] Show: name, position #1, last worked date, description, recent activity

---

## Protocol: Save Project

**Trigger**: `"save project"` -- saves current project only, NOT AI memory

### Step 1: Identify Active Project
- [ ] Check `main/current-session.md` for active project
- [ ] If no active project: inform user, suggest loading or creating one

### Step 2: Gather Session Progress
- [ ] Collect work done in current session
- [ ] Capture code changes, decisions, milestones

### Step 3: Parse Duration
- [ ] Read recent commit messages: `git log --oneline --format="%s%n%b" -20`
- [ ] Search for `Time:` field in commit bodies (from Auto-Commit System)
- [ ] Sum all `Time: ~XX min` values and add to project's accumulated duration

### Step 4: Update Project File
- [ ] Update "Last Accessed", "Duration", "Current Status"
- [ ] Add session entry to Session History

### Step 5: Line Limit Check
- [ ] If over 1000 lines: summarize old sessions, keep last 5

### Step 6: Update Project List
- [ ] Regenerate `projects/project-list.md`

### Step 7: Confirm Save
- [ ] Display: project name, saved timestamp, session summary, total duration

---

## Protocol: List Projects

**Trigger**: `"list projects"` or `"show projects"`

### Step 1: Read Project List
- [ ] Load `projects/project-list.md`

### Step 2: Display
- [ ] Show active projects with position, name, last updated, status
- [ ] Show archived project count and names
- [ ] Highlight currently loaded project (if any)

---

## LRU Engine

- **Fixed Capacity**: 10 active projects (positions 1-10)
- **Auto-Archiving**: Position #11 gets archived automatically
- **Reactivation**: Archived projects can be loaded back at any time

---

## Embedded Project Template

```markdown
# [Project Name] - [Brief Description]
*[One-line project summary]*

## Project Overview
- **Type**: [Category: Web App/API/Library/Game/Tool/etc.]
- **Period**: [Start Date] - Active
- **Tech Stack**: [Backend] + [Frontend] + [Database]
- **Completion**: 0%
- **Duration**: 0 min

## Current Status
- **Last Session**: [Date] - Project created
- **Next Steps**: [Initial goals]
- **Known Issues**: None

## Session History (Last 5)

### [Date] - Project Created
- **Changes**: Initial project setup
- **Time Spent**: ~0 min

## Historical Summary
[No history yet -- this section is populated when session count exceeds 5]

## Technical Notes
- **Repository**: [Git URL or local path]
- **Key Dependencies**: [Critical packages or services]

---
**Last Updated**: [Date] | **Position**: #1/10 Active
```

---

## Mandatory Rules

1. **10 active slots** -- auto-archive at position #11
2. **project-list.md regenerated** after every LRU operation
3. **Line limit 1000** -- auto-summarize when exceeded, keep last 5 sessions
4. **Duration tracking** -- parse `Time:` from Auto-Commit messages, accumulate per project
5. **"save project" is project-only** -- does NOT save AI memory or preferences
6. **Explicit save only** -- no auto-save. User controls when to save
7. **Fuzzy search on load** -- partial names, case-insensitive matching

## Level History
- **Lv.1** -- Base: new/load/save/list commands, LRU engine, auto-archiving, session history, project-list.md auto-generation.
- **Lv.2** -- Duration Tracking + Line Limit Enforcement (1000-line cap with auto-summarization).
