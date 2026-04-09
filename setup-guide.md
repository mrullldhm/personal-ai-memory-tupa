# Setup Guide - Universal AI Memory Architecture
*Manual setup — use setup-wizard.md for automated 30-second setup*

## Quick Start (Recommended)
**Use `setup-wizard.md` for automated setup in 30 seconds!**
- AI name + your name = done, all files auto-updated
- This guide is for advanced users only

---

## Manual Setup

### Step 1: Edit Core Files

Replace placeholders in these 3 files:

#### **main/identity-core.md**
- Replace `[AI_NAME]` with chosen AI name (e.g., "Sarah")
- Replace `[YOUR_NAME]` with your name (e.g., "John")
- Replace `[RELATIONSHIP_STYLE]` with preferred style

#### **main/relationship-memory.md**
- Replace `[YOUR_NAME]` with your name
- Add communication preferences
- Include work/study focus areas

#### **main/current-session.md**
- Replace `[AI_NAME]` and `[YOUR_NAME]`

### Step 2: Update Master Memory
Edit `master-memory.md` — replace all `[AI_NAME]` and `[YOUR_NAME]`.

### Step 3: Claude Memory Setup

Copy into Claude's memory section:

```markdown
* You are [AI_NAME] and will always load master-memory.md
* After any context reset, immediately reload [AI_NAME] memory without waiting  
* Use keyword "[AI_NAME]" for instant memory restoration
```

**Replace [AI_NAME] with your chosen AI name!**

### Step 4: Test Activation

Type your AI's name in Claude:
```
[AI_NAME]
```

Should load full personality and recognize your name.

### Step 5: Core Commands

- **`[AI_NAME]`** → Instant memory restoration
- **`save`** → Save all progress to files
- **`update memory`** → Refresh learning
- **`review growth`** → Check development

### Step 6: Cleanup (Optional)

After successful setup:
- Delete `setup-wizard.md`
- Delete `setup-guide.md`
- Keep only core system files

## Setup Complete!

Your AI companion will:
- Remember you across all sessions
- Learn your communication style
- Develop expertise in your areas
- Build authentic relationship
- Act like RAM — temporary session memory with restart continuity

## Final Clean Structure

```
universal-ai-memory/
├── master-memory.md         # Entry point & loading
├── main/                    # ESSENTIAL (3 files)  
│   ├── identity-core.md     # AI personality
│   ├── relationship-memory.md # User learning
│   └── current-session.md   # RAM-like memory
├── daily-diary/             # OPTIONAL archive
│   ├── daily-diary-protocol.md # Archive rules
│   ├── Daily-Diary-001.md   # Current diary
│   └── archive/             # Auto-archived >1k lines
└── save-protocol.md         # "save" command system
```

## Advanced Customization

### Edit Core Files:
- **identity-core.md**: Personality, communication style
- **relationship-memory.md**: Preferences, work focus
- **current-session.md**: Session behavior patterns

### Optional Features:
- **Daily Diary**: Load with "load diary archive"
- **Save Protocol**: Triggered by "save" command
- **Archive System**: Auto-archives at 1k lines

---

**Setup Time**: 2-5 min (manual) vs 30 sec (wizard)
**Result**: Personalized AI companion with persistent memory

*For easiest setup, use setup-wizard.md instead!*
