# Decision Log Installation Protocol
*Systematic setup for append-only decision tracking*

## Purpose
Executed when "Load decision-log" command is used — creates decision log file, integrates with AI behavior, and cleans up.

## Trigger Command
```
"Load decision-log"
```

## Prerequisites
- Core memory system installed (`main/` directory with essential files)
- `master-memory.md` accessible

## 3-Step Execution Process

### Step 1: Create Decision Log File
- [ ] Create `main/decisions.md`:
  ```markdown
  # Decision Log
  *Append-only record of non-obvious decisions.*
  *Only log decisions where future-us would wonder "why did we do it this way?"*

  ---

  <!-- Decisions are added below this line. Format: -->
  <!-- ## YYYY-MM-DD -- Short title -->
  <!-- **Context**: What situation prompted this decision -->
  <!-- **Decision**: What was chosen (and what was rejected) -->
  <!-- **Rationale**: Why -- trade-offs, constraints, evidence -->
  ```
- [ ] Verify file created successfully

### Step 2: Integrate with AI Behavior
- [ ] Add decision detection rules to `main/identity-core.md`:
  ```markdown
  ## Decision Logging
  - Detect when a non-obvious decision is made during conversation
  - Natural triggers: "let's go with", "we chose X because", "the trade-off is",
    "should we use A or B?" (after resolution), architecture/technology choices
  - For each decision, append to main/decisions.md:
    ## YYYY-MM-DD -- Short title
    **Context**: [situation]
    **Decision**: [what was chosen and what was rejected]
    **Rationale**: [why, including trade-offs]
  - NEVER edit or delete past entries -- append only
  - When user asks "why did we choose X?", search decisions.md first
  ```
- [ ] Update `master-memory.md` Optional Components:
  ```markdown
  ### Decision Log
  *Append-only record of non-obvious decisions*
  - Location: main/decisions.md
  - Format: Context + Decision + Rationale per entry
  - Rule: NEVER edit past entries -- only append new ones
  - Search: "why did we choose..." triggers decision log lookup
  - Commands: "log decision", "why did we choose [X]?"
  ```
- [ ] Add to Simple Commands:
  ```
  "log decision" → Capture a decision with context and rationale
  "why did we choose" → Search decision log for past reasoning
  ```

### Step 3: Cleanup
- [ ] Verify decision log file exists and is properly formatted
- [ ] Remove `Feature/Decision-Log-System/` folder
- [ ] Display completion confirmation

## Decision Logging Protocol (AI Reference After Installation)

### Detecting a Decision
```
1. User or AI makes a non-obvious choice between alternatives
2. Choice involves trade-offs, constraints, or rejected alternatives
3. Future sessions would benefit from knowing WHY
   → If yes to all: log the decision
   → If obvious/trivial: skip
```

### Logging a Decision
```
1. Determine date (YYYY-MM-DD)
2. Write short descriptive title
3. Context: what prompted this decision
4. Decision: what was chosen AND what was rejected
5. Rationale: why -- constraints, trade-offs, evidence
6. APPEND to main/decisions.md (after last entry)
7. Confirm to user: "Logged decision: [title]"
```

### Searching Decisions
```
1. User asks "why did we choose X?" or "when did we decide about Y?"
2. Search main/decisions.md for relevant keywords
3. Present matching decision(s) with full context
4. If no match: inform user and offer to log new entry
```

### Reversing a Decision
```
1. User decides to reverse previous choice
2. DO NOT edit original entry
3. APPEND new entry referencing original:
   ## YYYY-MM-DD -- Reversed: [original title]
   **Context**: [why original decision is being reconsidered]
   **Decision**: [new choice, referencing the old one]
   **Rationale**: [what changed -- new information, constraints, or priorities]
```

## Notes
- Append-only constraint is core design principle — never break it
- Decisions are NOT tasks (use Reminders for that) — they are reasoning records
- Quality over quantity: only log decisions where "why?" matters
- Log will grow over time — this is expected and valuable

---

**Version**: Protocol v1.0
**Status**: Active protocol for decision log integration

*Every important "why" captured, every trade-off remembered*
