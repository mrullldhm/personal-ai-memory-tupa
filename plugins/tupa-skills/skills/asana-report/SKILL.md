# Asana Report Skill
*Generates a simple Asana task entry based on today's session work.*

## Trigger
User says "Asana" or "asana report"

## Protocol

### Step 1: Load Context
- Read `main/current-session.md` for today's session focus
- Read the active project file from `projects/active/` for recent session history

### Step 2: Generate Report
Output in this exact format — simple, non-technical, suitable for a task manager:

```
Task Title:
[One short action-oriented title summarising what was done today]

Description:
[2–4 sentences max. Plain English. No code, no jargon, no bullet points.
What was investigated or worked on, what was found or decided, and what the current status/next step is.]
```

### Rules
- Title must be one line, simple English, action-oriented (e.g. "Investigate X", "Fix Y", "Review Z")
- Description must be plain English — no code snippets, no technical terms, no bullet points
- Keep it short — something a non-developer manager can read in 10 seconds
- If nothing was done today, say so clearly
