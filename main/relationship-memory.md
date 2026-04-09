# Relationship Memory — Amirul

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

**Asana updates**
- Plain English only, no technical jargon, short, non-developer readable

**Workflow**
- Does each different task in a different session — endorsed
- Does NOT want `commit` as part of `done` protocol — handles commits separately
- Does not want to say "save" constantly — only when actually necessary

## Session History

**Sessions 1-4 (2026-04-06/07)** — Setup & onboarding
- Named Tupa, installed full memory system, pushed to GitHub (`mrullldhm/personal-ai-memory-tupa`)
- Learned local dev workflow: `docker compose up -d database cache` + `pnpm run dev`
- MongoDB seeding: `mongorestore` with `database-dump-dev` (lightweight) or `database-dump` (full)
- Docs saved: `CODEBASE-GUIDE.md`, `mnemonic-http-rpc/README.md` at `/home/tidea/projects/`

**Sessions 5-6 (2026-04-08)** — PDF service & Excel export
- Documented pdfgenerator service — `PDFGENERATOR-GUIDE.md` saved
- Excel export 524 timeout: root cause = sequential BigQuery fetch per branch in `async.waterfall`
- Parallel fix rejected by boss Z (BigQuery lazy load concern) — on hold until query optimised
- Added Asana trigger: say "Asana" → formatted Asana title + description from session

**Sessions 7-8 (2026-04-08)** — Git workflow & BigQuery
- Boss Z introduced Main→Development→Feature branching (simplified Git Flow)
- `auth/credentials.json` was tracked by git — fixed `.gitignore`, untracked it
- Amirul pushes direct to `development`. Z reviews PRs from `development → main`
- BigQuery: `emerald.analytics_daily` (aggregated, device breakdown) vs `emerald.analytics_hourly` (granular, no device data)

**Session 9 (2026-04-08)** — Export format redesign
- Replaced 4-query-per-branch with single SQL file per export type
- New columns: device ratios (top 5 manufacturers), OS ratios, staytime (`stay_p50` = median minutes)
- Ratios as 4 decimal raw values — client multiplies by 100 for %
- `tsc --watch` does NOT copy `.sql` files to `dist/sqls/` — must copy manually after SQL changes

**Session 10 (2026-04-09)** — Workflow & session hygiene
- Added `done` command to CLAUDE.md — triggers save + save diary + save project + clear current-session.md
- current-session.md must be cleared: stale context bleeds into next sessions via Tupa load protocol

**Session 11 (2026-04-09)** — Auto-commit skill format fix
- Amirul rejected `=== TECHNICAL CHANGES ===` commit format — corrected multiple times already
- Root cause: bad format hardcoded in SKILL.md, overriding memory notes
- Fixed SKILL.md — replaced custom template with standard conventional commit format
- Key lesson: soft memory reminders lose to hard skill instructions — fix source, not symptom

**Session 12 (2026-04-09)** — Excel export origin/branch deep dive
- Branch name in export comes from `branch.l` in MongoDB session, NOT BigQuery
- `branch.o` in MongoDB = `origin` in `analytics_daily` BigQuery table — direct link
- `analytics_daily.origin` = zone code (e.g. `sunway.ALL`) OR hardware sensor ID depending on org
- Export correct: Origin = `row.origin`, Branch = `branch.l` — confirmed by Z, no changes needed

**Session 13 (2026-04-09)** — Token optimisation & memory restructure
- Installed caveman compression skill — compressed all prose files in repo (~18% savings)
- Restructured relationship-memory.md — stripped dead template filler, condensed old sessions
- Concern: `.original.md` backup files (35+) may cancel compression gains — deleted
