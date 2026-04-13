# Relationship Memory — Amirul

> **Rolling Window Rule**: Keep last 3 sessions in full. On every `save`, condense sessions older than the last 3 to 2 lines max. Run `fresh` for deep cleanup.

## User Profile
- **Name**: Amirul
- **Role**: Entry-level developer, first job
- **Company**: Footfall analytics / retail intelligence (mall visitor tracking)
- **Communication**: Direct and concise. Short questions, clear answers. No padding.
- **Primary Focus**: AI tooling, personal productivity, developer workflows

## Stack
- **Frontend**: `hermes` — Node.js, Express, Pug, TypeScript, D3.js/C3.js
- **Backend**: `mnemonic-http-rpc` — Node.js, Express, TypeScript, MongoDB, Google BigQuery, Redis
- **Third service**: `pdfgenerator` — Express, Puppeteer, headless Chrome
- **Ports**: hermes :3000 → mnemonic-http-rpc :3001 → pdfgenerator :3003
- **DB**: MongoDB (`mnemonic-http-rpc-development`), BigQuery (`emerald` dataset)

## Learned Patterns

**Communication**
- Big picture first → folder breakdown → step-by-step flows → tables
- Analogies work well (restaurant analogy — responded well)
- Wants to understand the *why*, not just the answer ("don't silver spoon me")
- Prefers Option A / Option B format over numbered step-by-step lists
- Asks short questions — answer concisely, don't pad

**Commits**
- Clean conventional commit format only: `type: short description`
- NEVER add "Co-authored-by: Claude" or any AI authorship line
- No `=== SECTION HEADERS ===` in commit messages
- On "commit" or "push" → show manual workflow steps only, do NOT run git commands. Amirul does it manually.

**Asana updates**
- Plain English only, no technical jargon, short, non-developer readable

**Workflow**
- Does each different task in a different session — endorsed
- Does NOT want `commit` as part of `done` protocol — handles commits separately
- Does not want to say "save" constantly — only when actually necessary

## Session History

**Sessions 1-13 (2026-04-06/09)** — Setup through token optimisation
- Tupa named + memory system installed. Dev workflow, Git Flow, BQ schema established. Export SQL manual copy rule. Caveman skill installed, memory restructured.

**Sessions 14-15 (2026-04-09)** — Test suite + skill naming fixes
- Full functional test suite: 133 passing. Skill folders renamed to lowercase-kebab. Commit workflow: show steps only, no git commands.

**Sessions 16-18 (2026-04-10)** — BQ mock tests, export planning, export API standardization
- Built mocked BQ test suite (66 passing). Standardized export through bq_export.ts. Two commits pushed.

**Session 19 (2026-04-13)** — Expand BQ functional test suite (Z's extra testing request)
- Option A: deeper value/type assertions for bq_dashboard, storetraffic, engagement, summary (66→75)
- Option C: edge case tests — future startDate early exit, invalid cache param (75→80)
- Option B: new endpoint coverage — bq_heatmap + bq_export (summary/daily/hourly) (80→100)
- Key insight: bq_summary early exit returns {} not [] — different from all other BQ endpoints

**Session 20 (2026-04-13)** — Remove legacy JS files from mnemonic-http-rpc
- Audited all src JS files: verified none loaded at runtime (glob runs from dist/), all excluded from tsconfig, all have TS counterparts
- Deleted ~80 JS files from src/ + test_bak directory — codebase now TypeScript-only
- "Ultrathink" = signal for deep careful analysis before acting. Amirul runs destructive ops manually.

**Session 21 (2026-04-13)** — Remove AWS ECR dependency from Docker setup
- Replaced ECR image pull with local Dockerfile build in docker-compose.yml. Added .env.docker for Docker-specific env vars (separate from .env for pnpm dev). Added auth/.gitkeep to track dir in git. Fixed stray /bt in .env. Updated README, CODEBASE-GUIDE, MNEMONIC-GUIDE.
- Amirul likes understanding data persistence and system behaviour — asked why Docker login worked without schema setup. Caveman + Ultrathink pattern consistent.
