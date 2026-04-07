# TIDE Codebase Onboarding - Understanding the company platform
*Learning and documenting the full TIDE Analytics platform codebase*

## Project Overview
- **Type**: Onboarding / Documentation
- **Period**: 2026-04-06 - Active
- **Tech Stack**: Hermes (Express/Pug) + mnemonic-http-rpc (TypeScript/Express) + MongoDB + BigQuery + Redis
- **Completion**: 30%
- **Duration**: ~90 min

## Current Status
- **Last Session**: 2026-04-07 - Port fix + git workflow intro
- **Next Steps**: Start reading the learning roadmap files (app.js → config → express → controllers). Try running both repos locally.
- **Known Issues**: AWS ECR credentials needed for full Docker setup — use Option B (pnpm dev) instead.

## Session History (Last 5)

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
**Last Updated**: 2026-04-07 | **Position**: #1/10 Active
