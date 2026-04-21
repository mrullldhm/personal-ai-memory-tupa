# Relationship Memory — Amirul

> Rolling Window Rule: keep last 3 sessions full. Condense older to 2 lines max. Run `fresh` for deep cleanup.

## User Profile
- Name: Amirul
- Role: Entry-level dev, first job
- Company: Footfall analytics / retail intelligence (mall visitor tracking)
- Communication: Direct, concise. No padding.
- Focus: AI tooling, personal productivity, dev workflows

## Stack
- Frontend: `hermes` — Node.js, Express, Pug, TypeScript, D3.js/C3.js
- Backend: `mnemonic-http-rpc` — Node.js, Express, TypeScript, MongoDB, BigQuery, Redis
- Third service: `pdfgenerator` — Express, Puppeteer, headless Chrome
- Ports: hermes :3000 → mnemonic-http-rpc :3001 → pdfgenerator :3003
- DB: MongoDB (`mnemonic-http-rpc-development`), BigQuery (`emerald` dataset)

## Learned Patterns

**Communication**
- Big picture first → folder breakdown → flows → tables
- Analogies work well (restaurant analogy)
- Wants *why*, not just answer ("don't silver spoon me")
- Prefers Option A / Option B over numbered steps
- Short questions → concise answers, no padding

**Teaching / Explaining**
- A to Z, nothing skipped — every detail matters
- Fresh grad mindset — needs time to process, no assumed knowledge
- Ambition: wants to be one of best devs, not just get by
- Don't spoon-feed — explain *why* behind every decision
- Flow: big picture → file map → step-by-step → tables → edge cases
- Confirmed style after Export Spreadsheet explanation (2026-04-21)

**Commits**
- Clean conventional format only: `type: short description`
- NEVER add "Co-authored-by: Claude" or any AI authorship line
- No `=== SECTION HEADERS ===` in commit messages
- On "commit"/"push" → show manual workflow steps only, don't run git

**Asana**
- Plain English, no jargon, short, non-dev readable

**Workflow**
- Each task = different session — endorsed
- Does NOT want `commit` in `done` protocol — handles separately
- Doesn't want to say "save" constantly — only when necessary

## Session History

**Sessions 1-30 (2026-04-06/17)** — Foundation through report subscription
- Tupa setup, memory, Git Flow, BQ schema, test suites (133 functional + 100 BQ mocked), legacy JS cleanup, Docker, export UI, hourly CSV, LinkedIn. PDF + CSV email subscriptions built + e2e tested. Lesson: always `ls -la` all service dirs for .env files.

**Session 31 (2026-04-20)** — CSV subscription branch filter bug
- Option B: csvBranches lifted before generator call. Option A (OrganizationSchema) closed — solved without it.

**Session 32 (2026-04-20)** — Graphify maintenance
- Manifest saved (4,399 files), temp cleaned. No re-extraction needed — no code changes since 2026-04-17.

**Session 33 (2026-04-20)** — Graphify removed
- Not useful: vendor JS drowned app nodes. Removed graphify-out/, CLAUDE.md RAG section, done-protocol step 5, skill folder. rtk: 87% savings, 190K tokens.

**Session 34 (2026-04-21)** — Report Subscription deep-dive + Origin/Location fix
- A-to-Z subscription flow explained. Fixed Origin: processDailyV2/processHourlyV2 now 3-arg (row, branchOrigin, branchLabel). user.reportBranches confirmed dead.

**Session 35 (2026-04-21)** — Report Subscription test mechanism + CSV date range bug fix
- Taught full A-to-Z of how to test emailer. Correct command: `cd hermes && LOG_LEVEL=debug node -r dotenv/config reports/emailer.js --unit week --organization "Sunway Square"` (run from hermes/ root, not reports/).
- Found + fixed CSV date range bug: `generateCsvContent` got raw `start`/`end` (single day) while generator.js normalizes internally. Added `csvStart`/`csvEnd` normalization in emailer.js. Weekly: Apr 13–19, monthly: Mar 1–31. Z approved.

**Session 36 (2026-04-21)** — Z feedback: Mall PDF + column reorder + rename + export.js bug fix
- Implemented 3 Z feedback items + 1 regression fix.
- Feedback 1 (PDF only): all-branch → 1 PDF using `.all` origin branch (fallback: `org.b[0]`). CSV always uses all `org.b`. `--branch`: both PDF + CSV use that branch only.
- Feedback 2 (both spreadsheets): daily CSV reordered — all 5 device names grouped first, then all 5 ratios. `toFixed(4)` → `toFixed(2)` on all ratio values.
- Feedback 3 (both spreadsheets): column titles → `1st Device`…`5th Device` / `1st Device Ratio`…`5th Device Ratio`.
- Bug: `export.js` calling `processDailyV2(row, branch.l)` — 2 args (regression from session 34). Fixed to `(row, branch.o, branch.l)` for both daily + hourly.
- Fixed `csvStart`/`csvEnd` regression in `emailer.js` line 199 — had reverted to raw `start`/`end`.

**Session 37 (2026-04-21)** — excels.js → csv.js rename
- Option A closed (no OrganizationSchema change needed). Renamed `excels.js` → `csv.js`: updated index.js barrel, export.js, emailer.js variable names + HERMES-GUIDE.md and CLAUDE.md docs. All tests passed.
