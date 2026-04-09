# Memory Consolidation System
*Unified memory architecture for faster loading and better context*

## What This Feature Does
Upgrades AI MemoryCore from split memory files to single unified memory:

- **Merges identity + relationship** into one unified `main-memory.md`
- **Adds session memory format template** for consistent structure after resets
- **Adds main memory format template** for consistent structure reference
- **Adds 500-line limit** to session memory with RAM-style reset
- **Faster restoration** — loads 1 file instead of 2
- **Bundled patch system** — AI-executable patches to fix outdated references

## Why Consolidate?

### Before (Split Architecture)
```
master-memory.md            ← Loader (reads 2 files)
main/identity-core.md       ← AI personality ONLY
main/relationship-memory.md ← User preferences ONLY
main/current-session.md     ← Session RAM (no size limit)
```
**Problems:**
- 3 separate file reads at startup = slower restoration
- AI identity and user understanding disconnected
- Session memory can grow indefinitely
- No format reference when session resets

### After (Unified Architecture)
```
master-memory.md               ← Loader (reads 1 file)
main/main-memory.md            ← AI identity + User profile + Relationship (UNIFIED)
main/current-session.md        ← Session RAM with 500-line limit + reset protocol
main/main-memory-format.md     ← Permanent format reference for main memory
main/session-format.md         ← Permanent format reference for session memory
```
**Benefits:**
- Single file load = faster startup
- AI personality and user understanding stay together
- Session memory auto-resets at 500 lines (keeps recap only)
- Format templates ensure consistent structure after every reset

## Quick Integration
```bash
"Load memory-consolidation"
```

## What Happens During Integration

1. **Reads** existing `identity-core.md` and `relationship-memory.md`
2. **Merges** both into single `main/main-memory.md`
3. **Creates** format templates as permanent structure references
4. **Updates** `current-session.md` with 500-line limit and reset behavior
5. **Updates** `master-memory.md` to load new unified file
6. **Removes** old split files (`identity-core.md`, `relationship-memory.md`)
7. **Self-deletes** this feature folder after successful integration

## Format Templates

### `main-memory-format.md` (Sample)
Defines expected structure for unified main memory:
- Identity section (who the AI is)
- User profile section (who the user is)
- Communication style and relationship context
- Behavioral patterns and growth philosophy

### `session-format.md` (Sample)
Defines expected structure for session RAM:
- Session status and timestamps
- Working memory (current task, goals, progress)
- Session recap (for restart continuity)
- 500-line limit rule and reset behavior

Both templates are **permanent references** — never modified by AI. Live files (`main-memory.md`, `current-session.md`) follow these formats.

## Bundled Patch System

After consolidation, outdated file references may remain in other project files. Bundled patch system fixes these automatically.

### How Patches Work
Patches are AI-executable `.md` files with structured find/replace instructions. AI reads patch, locates exact text in target files, applies changes.

### Available Patches
| Patch | Title | Files Affected | Priority |
|-------|-------|---------------|----------|
| `PATCH-001` | Fix outdated file references | 5 files (master-memory, save-protocol, daily-diary-protocol, current-session, setup-wizard) | High |

### Applying Patches
```
"Load patch-system"
```

### Patch Commands (After Installation)
- `"apply patch [ID]"` — Read and apply specific patch
- `"check patches"` — List available unapplied patches
- `"patch status"` — Show applied patches log

---

*Load `consolidation-core.md` to upgrade to unified memory, then `Load patch-system` to fix stale references!*
