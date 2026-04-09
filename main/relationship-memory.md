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

**Sessions 1-12 (2026-04-06/09)** — Setup through export deep dive
- Tupa named + memory system installed. Dev workflow: `docker compose up -d database cache` + `pnpm run dev`. Mongo: `mongorestore` with `database-dump-dev`.
- Git Flow: Main→Development→Feature. Amirul pushes to `development`; Z reviews PRs to `main`. BigQuery: `emerald.analytics_daily` (aggregated) vs `emerald.analytics_hourly` (granular). Export uses single SQL per type; `tsc --watch` doesn't copy `.sql` — copy manually. Origin = `row.origin`, Branch = `branch.l` from MongoDB (confirmed by Z).

**Session 13 (2026-04-09)** — Token optimisation & memory restructure
- Installed caveman compression skill — compressed all prose files in repo (~18% savings)
- Restructured relationship-memory.md — stripped dead template filler, condensed old sessions
- Concern: `.original.md` backup files (35+) may cancel compression gains — deleted

**Session 14 (2026-04-09)** — Functional testing for mnemonic-http-rpc
- Set up full functional test suite: ping, org, user, campaign, common_visit, hermes_*, bq_*, v2 login
- Test DB isolation via setup.js (mnemonic-http-rpc-test), chai v4 (ESM constraint), mocha ^8
- 133 passing, 0 failing, 20 pending (legacy skipped unit tests — harmless)
- Hermes changes reverted cleanly; test/README.md written to industry standard
- Caveman skill created and wired into CLAUDE.md from JuliusBrussee/caveman
- Next session: mock bq_* data tests using Z's v3-metadata-data-structures SQL sample

**Session 15 (2026-04-09)** — Skill naming fix + workflow clarification
- All Feature/ skill folders renamed to lowercase-kebab (Ubuntu case-sensitive)
- post-mortem-system + session-briefing-system SKILL.md missing frontmatter — added
- Rule: folder name must exactly match `name` field in SKILL.md frontmatter, both lowercase-kebab
- On "commit" or "push": show manual workflow only, do not run git commands
