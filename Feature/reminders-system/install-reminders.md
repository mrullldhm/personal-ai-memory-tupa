# Reminders System Installation Protocol
*Systematic setup for persistent cross-session reminders*

## Purpose
Executed when "Load reminders" command is used — creates reminders file, integrates with session lifecycle, optionally installs as skill.

## Trigger Command
```
"Load reminders"
```

## Prerequisites
- Core memory system installed (`main/` directory with essential files)
- `master-memory.md` accessible

## 4-Step Execution Process

### Step 1: Create Reminders File
- [ ] Create `main/reminders.md`:
  ```markdown
  # Active Reminders
  *Persistent reminders that survive session changes. Updated at session end.*

  ## Open
  <!-- Active reminders go here. Format: -->
  <!-- - **Short title**: Description of what needs to be done -->
  <!-- - **Title** (by YYYY-MM-DD): Description with deadline -->

  ## Completed
  <!-- Resolved reminders move here. Format: -->
  <!-- - **Title** (completed YYYY-MM-DD): What was done and the outcome -->
  ```
- [ ] Verify file created successfully

### Step 2: Integrate with Session Lifecycle
- [ ] Update `master-memory.md` to include reminders in loading system:
  - Add to "Instant Restoration Protocol":
    ```markdown
    5. ✅ **Check reminders** from `main/reminders.md`
    ```
  - Add to "Simple Commands":
    ```
    "check reminders" → Review open reminders and flag urgent items
    "remind me" → Add a new reminder to the Open section
    ```
- [ ] Update `master-memory.md` Optional Components:
  ```markdown
  ### Reminders
  *Persistent cross-session follow-up tracking*
  - Location: main/reminders.md
  - Lifecycle: Open → Completed (with date)
  - Session start: Read and flag urgent/overdue items
  - Session end: Review, update, move completed items
  - Commands: "check reminders", "remind me [task]"
  ```

### Step 3: Define AI Behavior Rules
- [ ] Add to `main/identity-core.md` behavior section:
  ```markdown
  ## Reminder Management
  - At session start: read main/reminders.md, mention urgent or overdue items
  - At session end: review Open reminders, move resolved ones to Completed with date
  - During conversation: detect reminder-worthy phrases and offer to add them
  - Natural triggers: "remind me", "don't forget", "follow up", "next session",
    "by [date]", "check on this later"
  - Always convert relative dates to absolute (e.g., "tomorrow" → "2025-10-05")
  - Never delete reminders -- move to Completed section when resolved
  ```

### Step 4: Install Skill and Cleanup
- [ ] If Skill Plugin System exists:
  - Copy `SKILL.md` to `plugins/[plugin-name]/skills/check-reminders/SKILL.md`
  - Inform user: "Reminder skill installed"
- [ ] If Skill Plugin System does not exist:
  - Inform user: "Reminders integrated into master memory. Install Skill Plugin System for auto-triggering."
- [ ] Remove `Feature/Reminders-System/` folder
- [ ] Display completion confirmation

## Reminder Management Protocol (AI Reference After Installation)

### Adding a Reminder
```
1. User says something reminder-worthy (or explicitly asks)
2. Compose reminder with clear title and description
3. If deadline mentioned, convert to absolute date (YYYY-MM-DD)
4. APPEND to ## Open section in main/reminders.md
5. Confirm: "Added reminder: [title]"
```

### Completing a Reminder
```
1. Task done or no longer relevant
2. Remove from ## Open section
3. Add to ## Completed with completion date:
   - **Title** (completed YYYY-MM-DD): What was done
4. Confirm: "Marked as complete: [title]"
```

### Session Start Check
```
1. Read main/reminders.md
2. Count open reminders
3. Check for deadlines approaching (within 3 days) or overdue
4. If urgent items exist: mention naturally in greeting
5. If no urgent items: skip
```

### Session End Review
```
1. Read main/reminders.md
2. For each Open reminder: was it addressed this session?
3. Move completed items to Completed with date
4. Add new reminders discovered during session
5. Save updated file
```

## Notes
- Reminders persist independently from session memory — core design
- Always APPEND to Open, never overwrite
- Move completed items rather than deleting (creates searchable history)
- Convert all relative dates to absolute when saving
- Completed section can grow large — fine, serves as history

---

**Version**: Protocol v1.0
**Status**: Active protocol for reminders integration

*Persistent memory across sessions — nothing gets lost*
