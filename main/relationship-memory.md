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

**Session 16 (2026-04-10)** — BQ mock tests + test suite restructure
- Added mocked BigQuery functional tests for bq_dashboard, storetraffic, engagement, summary
- Created test/helpers/bq-mock.js (sinon stubs on hermes-bq module exports)
- Created test/fixtures/bq-responses.js *Processed shapes + analyticsDaily/analyticsHourly raw rows
- Created test/functional/v1/bq_connection.test.js (module load checks)
- Separated unit tests from pnpm test — unit tests now pnpm test:unit only (had 20 pending legacy skipped)
- Updated test/README.md to industry standard
- Pushed to development branch. 66 passing, 0 pending
- One-time git push permission granted for this session only

**Session 17 (2026-04-10)** — Export parallelization planning (no code changes)
- Reviewed all BQ workflows, planned for...of → Promise.all. Z changed direction → no code written.

**Session 18 (2026-04-10)** — Standardize Export Excel to bq_dashboard/bq_summary pattern
- Z's new direction: route export through dedicated /api/v1/bq_export instead of /bigquery directly
- Created mnemonic: bq_export.ts (follows bq_summary structure, uses validateBQRequest, createBQCacheWrapper)
- Added hermes-bq.ts: getExportSummary / getExportDaily / getExportHourly (call bigQuery.newQuery with export SQLs)
- Updated hermes export.js: 3 axios calls changed from /bigquery → /bq_export with exportType param
- Route auto-registered via glob — no index.ts change needed. SQLs unchanged. excels.js unchanged.
