# TIDE Codebase Onboarding - Understanding the company platform
*Learning and documenting the full TIDE Analytics platform codebase*

## Project Overview
- **Type**: Onboarding / Documentation
- **Period**: 2026-04-06 - Active
- **Tech Stack**: Hermes (Express/Pug) + mnemonic-http-rpc (TypeScript/Express) + MongoDB + BigQuery + Redis
- **Completion**: 45%
- **Duration**: ~195 min

## Current Status
- **Last Session**: 2026-04-09 - Excel export origin/branch data flow exploration
- **Next Steps**: Create `development` branch for `hermes` and `pdfgenerator` (still pending). Post Asana update for Session 9 export redesign work.
- **Known Issues**: AWS ECR credentials needed for full Docker setup — use Option B (pnpm dev) instead.

## Session History (Last 5)

### 2026-04-09 - Excel export origin/branch data flow
- **Focus**: How branch name/code flows through export pipeline
- **Outcome**: Traced `branch.o` (MongoDB) → `analytics_daily.origin` (BigQuery) → `row.origin` (CSV). Export correct. No code changes — verified with Z.
- **Learned**: `analytics_daily.origin` format varies by org — zone codes (`sunway.ALL`) or hardware sensor IDs (`E4956E444856`). Either way, `branch.o` always matches.
- **Time Spent**: ~15 min

### 2026-04-09 - Auto-commit skill format fix
- **Focus**: Tupa system fix (no code work)
- **Outcome**: Fixed `auto-commit/SKILL.md` — standard conventional commit format; eliminated `=== TECHNICAL CHANGES ===` template
- **Learned**: Soft memory reminders lose to hard skill instructions — fix must happen at source file
- **Time Spent**: ~10 min

### 2026-04-09 - Workflow & session hygiene setup
- **Focus**: Tupa workflow session (no code work)
- **Outcome**: Added `done` end-of-session command to CLAUDE.md — auto-runs save, save diary, save project, clear current-session.md
- **Learned**: Why current-session.md must be cleared between unrelated sessions (stale context bleeds in via Tupa load)
- **Time Spent**: ~15 min

### 2026-04-08 - BigQuery exploration — emerald dataset
- **Explored**: BigQuery Studio UI layout (project → dataset → table hierarchy)
- **Studied**: `emerald.analytics_daily` and `emerald.analytics_hourly` schemas
- **Key insight**: Both tables track foot traffic per location. `analytics_daily` = one row per (origin × day), includes device/manufacturer breakdown. `analytics_hourly` = one row per (origin × day × hour), ~24x more rows, no device breakdown
- **Assigned by**: Boss Z
- **No code changes** — purely educational
- **Time Spent**: ~30 min

### 2026-04-08 - Git branching + credentials security fix
- **Set up**: `development` branch on `mnemonic-http-rpc` — pushed to GitHub
- **Security fix**: `auth/credentials.json` tracked by git due to broken `.gitignore` line — fixed and untracked
- **Docs updated**: `MNEMONIC-GUIDE.md` and `README.md` — credentials must be obtained manually
- **Pending**: `hermes` and `pdfgenerator` development branches not yet created
- **Time Spent**: ~30 min

### 2026-04-08 - Excel export fix deferred + Asana trigger setup
- **Decision**: Boss confirmed fix on hold — BigQuery uses lazy load, parallel approach adds extra load
- **Added**: "Asana" trigger — generates plain-English Asana task title + description from session work
- **Skill Created**: `plugins/tupa-skills/skills/asana-report/SKILL.md`
- **Time Spent**: ~15 min

### 2026-04-07 - Excel export 524 timeout bug investigation
- **Bug**: `POST /export/all/summary` returns 524 (Cloudflare timeout) for large orgs. Small orgs work fine.
- **Root Cause**: `async.waterfall` in `hermes/app/controllers/export.js` fetches branches sequentially. Each BigQuery call ~5–15s. 10+ branches = 100s+ → exceeds Cloudflare 100s limit.
- **Fix Planned**: Replace waterfall with `async.map` (parallel) for `/all/summary`. Use `async.mapLimit(items, 5, ...)` for `/all/daily`.
- **Fix Status**: ON HOLD — boss decision. BigQuery lazy load; parallel approach adds extra load. Resume only after BigQuery query time optimised.
- **Key Files**: `hermes/app/controllers/export.js` (lines 181–353), `hermes/app/helpers/excels.js`, `excel-export@0.5.1`
- **Time Spent**: ~45 min

## Historical Summary
- **2026-04-07** - Port fix + git workflow: Fixed APP_PORT 3000→3001 in config, docker-compose, Dockerfile. Learned SSR reasoning and git branch rules. (~30 min)
- **2026-04-06** - Codebase deep dive + documentation: Created CODEBASE-GUIDE.md, HERMES-GUIDE.md, MNEMONIC-GUIDE.md. Learned full hermes + mnemonic-http-rpc architecture, data flow, visitor types, API versioning. (~60 min)

## Technical Notes
- **Repositories**:
  - Frontend: `hermes/` → separate GitHub repo
  - Backend: `mnemonic-http-rpc/` → separate GitHub repo
  - Both cloned locally under `/home/tidea/projects/`
- **Guide Files Created**:
  - `/home/tidea/projects/CODEBASE-GUIDE.md` — big picture overview (updated to include PDFGenerator)
  - `/home/tidea/projects/HERMES-GUIDE.md` — frontend sequential walkthrough
  - `/home/tidea/projects/MNEMONIC-GUIDE.md` — backend sequential walkthrough
- **Key Ports**: Hermes :3000, Backend :3001, PDFGenerator :3003
- **Key Config**: Backend API Key = `mnemonic-http-rpc-dev-secret-api-key`

---
**Last Updated**: 2026-04-09 (session 12) | **Position**: #1/10 Active
