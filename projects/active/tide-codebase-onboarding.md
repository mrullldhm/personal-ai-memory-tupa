# TIDE Codebase Onboarding - Understanding the company platform
*Learning and documenting the full TIDE Analytics platform codebase*

## Project Overview
- **Type**: Onboarding / Documentation
- **Period**: 2026-04-06 - Active
- **Tech Stack**: Hermes (Express/Pug) + mnemonic-http-rpc (TypeScript/Express) + MongoDB + BigQuery + Redis
- **Completion**: 45%
- **Duration**: ~180 min

## Current Status
- **Last Session**: 2026-04-08 - Git branching workflow setup + credentials security fix
- **Next Steps**: Create `development` branch for `hermes` and `pdfgenerator` (not done yet). Then start feature branch workflow for new tasks.
- **Known Issues**: AWS ECR credentials needed for full Docker setup — use Option B (pnpm dev) instead.

## Session History (Last 5)

### 2026-04-08 - Git branching + credentials security fix
- **Set up**: `development` branch on `mnemonic-http-rpc` — pushed to GitHub
- **Security fix**: `auth/credentials.json` was tracked by git due to broken `.gitignore` line — fixed and untracked
- **Docs updated**: `MNEMONIC-GUIDE.md` and `README.md` now document credentials must be obtained manually
- **Pending**: `hermes` and `pdfgenerator` development branches not yet created
- **Time Spent**: ~30 min

### 2026-04-08 - Excel export fix deferred + Asana trigger setup
- **Decision**: Boss confirmed fix is on hold — BigQuery uses lazy load, parallel approach would add extra load
- **Added**: "Asana" trigger to Tupa — generates a plain-English Asana task title + description from session work
- **Skill Created**: `plugins/tupa-skills/skills/asana-report/SKILL.md`
- **Time Spent**: ~15 min

### 2026-04-07 - Excel export 524 timeout bug investigation
- **Bug**: POST /export/all/summary returns 524 (Cloudflare timeout) for large orgs. Small orgs work fine.
- **Root Cause**: `async.waterfall` in `hermes/app/controllers/export.js` fetches branches sequentially. Each BigQuery call ~5–15s. 10+ branches = 100s+ → exceeds Cloudflare's 100s limit.
- **Fix Planned**: Replace waterfall with `async.map` (parallel) for `/all/summary`. Use `async.mapLimit(items, 5, ...)` for `/all/daily`.
- **Fix Status**: ON HOLD — boss decision. BigQuery uses lazy load; parallel approach would add extra load. Resume fix only after BigQuery query time is optimised.
- **Key Files**: `hermes/app/controllers/export.js` (lines 181–353), `hermes/app/helpers/excels.js`, `excel-export@0.5.1`
- **Time Spent**: ~45 min

### 2026-04-07 - Port fix + git workflow
- **Changes**: Fixed APP_PORT 3000 → 3001 in `src/config/config.js`, `docker-compose.yml`, `Dockerfile`
- **Learned**: Why frontend uses Express (SSR), git branch workflow (never commit to main), git push -u
- **Time Spent**: ~30 min

### 2026-04-06 - Codebase deep dive + documentation
- **Changes**: Created CODEBASE-GUIDE.md, HERMES-GUIDE.md, MNEMONIC-GUIDE.md in /home/tidea/projects/
- **Learned**: Full architecture of both repos — how Hermes and mnemonic-http-rpc connect, data flow, visitor types, multi-tenant structure, API versioning (V1 RPC vs V2 REST)
- **Time Spent**: ~60 min

## Historical Summary
*No old sessions to summarize yet.*

## Technical Notes
- **Repositories**:
  - Frontend: `hermes/` → separate GitHub repo
  - Backend: `mnemonic-http-rpc/` → separate GitHub repo
  - Both cloned locally under `/home/tidea/projects/` for convenience
- **Guide Files Created**:
  - `/home/tidea/projects/CODEBASE-GUIDE.md` — big picture overview (updated to include PDFGenerator)
  - `/home/tidea/projects/HERMES-GUIDE.md` — frontend sequential walkthrough
  - `/home/tidea/projects/MNEMONIC-GUIDE.md` — backend sequential walkthrough
- **Key Ports**: Hermes :3000, Backend :3001, PDFGenerator :3003
- **Key Config**: Backend API Key = `mnemonic-http-rpc-dev-secret-api-key`

---
**Last Updated**: 2026-04-08 (session 7) | **Position**: #1/10 Active
