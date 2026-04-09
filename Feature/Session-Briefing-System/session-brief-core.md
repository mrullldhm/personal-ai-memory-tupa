# Session Brief — Core Protocol

## When to Run
At start of every session, before processing user's first request.

---

## Step-by-Step Execution

### Step 1: Load Context
Read the following files (in parallel if possible):

| File | Purpose | Required |
|------|---------|----------|
| `main/current-session.md` | Last session recap | Yes |
| `main/reminders.md` | Open reminder items | Optional |
| Project list file | Active project + idle days | Optional |
| Current time | Time period classification | Optional |

### Step 2: Classify Time Period

| Time | Period | Work Suggestion |
|------|--------|----------------|
| 06:00–11:59 | Morning | Architecture, new features, complex problems |
| 12:00–17:59 | Afternoon | Implementation, debugging, testing |
| 18:00–21:59 | Evening | Code review, docs, moderate tasks |
| 22:00–05:59 | Night | Light tasks, planning — suggest wrapping up |

*Requires Time-based-Aware-System. If not installed, skip work suggestion line.*

### Step 3: Identify Attention Flags
Check project list for projects idle beyond their threshold:

| Flag | Meaning | Default Threshold |
|------|---------|------------------|
| 🟡 | Idle — approaching warning | 14 days |
| 🔴 | Stale — past critical threshold | 30 days |

- Show maximum 3 flags
- If more exist, show most critical (most days idle) first
- Skip section entirely if no projects flagged
- *Requires LRU-Project-Management-System. If not installed, skip.*

### Step 4: Compose Brief

```
📋 Session Brief · [Time Period]

Last session: [1–2 line recap from current-session.md]
Active: [project name] · [status]
🔴/🟡 [project name] — [N] days idle
Reminders: [N] open → [first item preview]
Suggestion: [time-appropriate work type]
```

**Composition rules:**
- Total lines: 12 maximum
- Omit any line/section with nothing to report
- "Last session" is the only mandatory line

### Step 5: Deliver
Output brief before processing user's first request.

---

## Minimal Version (Standalone — No Companion Systems)

If no companion systems installed:

```
📋 Session Brief

Last session: [recap from current-session.md]
```

---

## Threshold Customization

Edit Step 3 thresholds to match your workflow:
- Change `14` and `30` day defaults to any values preferred
- If using LRU-Project-Management-System with project tiers, apply tier-specific thresholds
