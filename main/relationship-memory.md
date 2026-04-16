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

**Session 19 (2026-04-13)** — BQ test suite 66→100: deeper assertions (A), edge cases (C), new endpoints bq_heatmap + bq_export (B). bq_summary early exit returns {} not [].

**Session 20 (2026-04-13)** — Remove legacy JS files from mnemonic-http-rpc
- Deleted ~80 legacy JS files from src/ + test_bak. Codebase now TypeScript-only. "Ultrathink" = deep careful analysis signal; Amirul runs destructive ops manually.

**Session 21 (2026-04-13)** — Remove AWS ECR dependency from Docker setup
- Replaced ECR image pull with local Dockerfile build in docker-compose.yml. Added .env.docker for Docker-specific env vars (separate from .env for pnpm dev). Added auth/.gitkeep to track dir in git. Fixed stray /bt in .env. Updated README, CODEBASE-GUIDE, MNEMONIC-GUIDE.
- Amirul likes understanding data persistence and system behaviour — asked why Docker login worked without schema setup. Caveman + Ultrathink pattern consistent.

**Session 22 (2026-04-14)** — Correct docker setup: gitignored dev docker-compose
- Discovered session 21 docker commit was wrong — Z wanted dev-only gitignored setup, not committed to repo.
- Reverted 90975f0. Created docker-compose-example.yml (ECR reference, committed) + docker-compose.yml (local build, gitignored). Updated .gitignore + README.md.
- Tupa missed "done" end-of-session protocol — must always trigger on "done" keyword regardless of conversation context.

**Session 23 (2026-04-15)** — Hourly Spreadsheet export + radio buttons on hermes export page
- Replaced 2 checkboxes with 4 radio buttons (PDF Report, Summary Spreadsheet, Daily Spreadsheet, Hourly Spreadsheet). Branch Location dropdown now conditionally shows only under PDF radio via `toggle(this.value === 'pdf')`.
- Z writes code, Tupa reviews and teaches why. Z caught naming issue (Excel → Spreadsheet). Tupa caught ë typo, duplicate row bug. Z wants to learn deeply, not be spoon-fed.

**Session 24 (2026-04-16)** — Remove Summary Spreadsheet from export feature
- Removed summary export end-to-end: radio button, actionMap entry, /all/summary route, excels helpers, bq_export.ts branch, getExportSummary(), export-summary.sql, tests + fixtures.
- Tupa taught removal methodology: trace feature top-to-bottom, delete bottom-up, grep-verify after. Caught stale `exportType: 'summary'` hiding in auth test — reinforced "never assume manual removal is complete without grep."
- Z learns by doing: implements himself, Tupa reviews. 96 tests passing.

**Session 25 (2026-04-16)** — Hourly export: all locations + bug fixes
- Changed hourly CSV from single-branch to all-branches (mirrors daily pattern). Renamed Branch→Location in daily CSV header. Fixed silent bug: row.returning_ truncated → row.returning_count.
- Z implemented himself, made 5 bugs: truncated property, branches.o vs branch.o (loop var), respondse typo, Math.ceil vs Math.floor, _hourly filename suffix. Tupa caught all 5.
- Teaching: trace data SQL alias → processor, loop variable discipline, typo grep check, Math.floor vs ceil for HHmm. Z fixed all correctly second attempt.
