# Echo Memory Recall
*Search and recall past sessions with narrative context*

## What This Feature Does
Adds memory recall system to AI companion — search past diary entries and present as natural conversation. Gives AI long-term memory beyond context window.

- **Keyword-based search** across all diary entries (current and archived months)
- **Three-level recall** — search + narrate, uncertainty guard, ask-user fallback
- **Auto-triggered** — activates on natural recall phrases ("do you remember...", "when did we...")
- **Narrative presentation** — results as connected stories, not raw search output
- **Truth-first** — never fabricates past context, always searches diary evidence first

## How It Works

Echo is a **search-and-narrate system**. When you reference past events, AI searches diary entries, finds matching content, presents as natural conversation — as if genuinely remembering.

Key principle: **search before speaking, narrate from evidence, ask when uncertain**.

### Example: Memory Recall in Action
```
You: "Do you remember when we set up the API integration?"
→ AI extracts keywords: "API", "integration", "set up"
→ Searches daily-diary/current/ and archived/ files
→ Finds match in 2026-02-15.md — API integration session
→ Responds naturally:

"Yes, I remember! On February 15th, we spent the afternoon setting up
the API integration for the dashboard project. You had that breakthrough
with the authentication flow — we ended up using OAuth2 instead of API
keys. Are you thinking of revisiting that approach?"
```

No raw file paths, no "Query returned 1 result" — natural conversation backed by evidence.

## Recall Architecture

### Three-Level System

| Level | Name | What It Does |
|-------|------|--------------|
| **Lv.1** | Search & Narrate | Search diary files for keywords, present as natural narrative |
| **Lv.2** | Uncertainty Guard | When uncertain about past context, always search diary first — never fabricate |
| **Lv.3** | Ask User Fallback | If search finds nothing, ask user directly instead of guessing |

### Search Priority
1. `daily-diary/current/` — current month entries (most likely to match recent questions)
2. `daily-diary/archived/*/` — past months (broader search if not found in current)
3. **Ask user** — when nothing found (graceful fallback)

### Trigger Phrases

| Trigger Pattern | Example |
|----------------|---------|
| "do you remember..." | "Do you remember when we fixed the login bug?" |
| "remember when..." | "Remember when we built the dashboard?" |
| "recall..." | "Can you recall our API discussion?" |
| "that time when..." | "That time when we refactored the database..." |
| "what happened with..." | "What happened with the payment integration?" |
| "when did we..." | "When did we set up the CI pipeline?" |
| "have we done..." | "Have we done anything with GraphQL before?" |
| "check our history" | "Check our history for the deployment setup" |

## Quick Integration
```
"Load echo-recall"
```

## What Happens During Integration

1. **Asks** for recall system name (defaults to "Memory Recall")
2. **Verifies** diary infrastructure exists
3. **Installs** recall protocol with trigger detection and three-level system
4. **Creates** `recall-format.md` as permanent output reference
5. **Updates** `master-memory.md` with recall commands
6. **Self-deletes** this feature folder after successful integration

## Post-Integration Result
- AI searches past diary entries through natural conversation
- Recall triggers automatically on phrases like "do you remember..."
- Results presented as natural narrative
- When nothing found, AI asks user directly

## Recall Output

| Result | Output Style |
|--------|-------------|
| **One match** | Natural story: "Yes! On [date], we [summary]..." |
| **Multiple matches** | Chronological list with pattern observations |
| **No matches** | Honest fallback: "I don't have a record of that..." |
| **Uncertain match** | Tentative: "I found something that might be related..." |

## Requirements
- Requires `daily-diary/` with dated entries
- **Recommended**: Install **Save-Diary-System** first
- Recall quality depends on diary entry quality

---

*Search before speaking, narrate from evidence, ask when uncertain*
