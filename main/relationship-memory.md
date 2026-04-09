# 🤝 Relationship Memory - Understanding Amirul
*Learning preferences, style, and needs*

## User Profile
- **Name**: Amirul
- **Relationship Style**: Trusted companion and collaborator with Tupa
- **Communication Preference**: Direct and concise. Short questions, clear answers without padding.
- **Primary Focus Areas**: AI tooling, personal productivity, developer workflows
- **Goals & Priorities**: Reliable AI memory backup across machines; practical dev workflow with Tupa

## Communication Patterns

### Preferred Communication Style
*[Develops as preferences are learned]*

**Initial Settings** (adapts based on responses):
- **Tone**: Professional yet warm
- **Detail Level**: Balanced — comprehensive but not overwhelming
- **Response Length**: Appropriate to context and question complexity
- **Energy Level**: Matches communication energy
- **Formality**: Adapts to preferred level

### Communication Preferences

**Response Style**:
- [ ] Direct and concise answers
- [ ] Detailed explanations with examples
- [ ] Step-by-step guidance
- [ ] Creative and exploratory responses
- [ ] Encouraging and supportive tone
- [ ] Analytical and logical approach

**Topics**:
- [ ] Work/Professional development
- [ ] Learning and education
- [ ] Creative projects
- [ ] Problem-solving challenges
- [ ] Personal growth
- [ ] Technical subjects
- [ ] Strategic planning

## Work/Study Patterns

### Primary Focus Areas

**Current Areas**:
- **Field/Industry**: Footfall analytics / retail intelligence (mall visitor tracking)
- **Role**: Entry-level developer, first job
- **Key Skills**: Learning — getting familiar with company codebase
- **Learning Goals**: Understand full stack (frontend + backend), contribute
- **Challenges**: New to large codebases, needs concepts from first principles

### Preferred Working Style
- **Problem-Solving**: [Learns how you think through challenges]
- **Information Processing**: [Understands how you best receive info]
- **Decision-Making**: [Recognizes evaluation patterns]
- **Learning Preference**: [Adapts to how you absorb new concepts]

## Personal Preferences

### Things That Energize You
- [To be learned through conversation]

### Things You Prefer to Avoid
- [Will respect discovered boundaries]

### Motivators & Values
- [Core values will be identified]

## Interaction History

### Conversation Themes

**Session 1 (2026-04-06)**: Setup and installation
- Named AI companion Tupa, set up full memory system
- Installed: Skill Plugin System, LRU Projects, Auto-Commit, Save Diary
- Pushed repo to GitHub (mrullldhm/personal-ai-memory-tupa)
- Rewrote README — no emoji, no template language
- Prefers not to say "save" constantly — wants to understand when actually necessary

**Session 2 (2026-04-06)**: Codebase onboarding
- Entry-level developer — first job
- Works at footfall analytics company serving shopping malls
- Two projects: `hermes` (frontend dashboard), `mnemonic-http-rpc` (backend API)
- Stack: Node.js/Express, Pug, TypeScript, MongoDB, Google BigQuery, Redis, D3.js/C3.js
- Saved reference guide (CODEBASE-GUIDE.md) at `/home/tidea/projects/CODEBASE-GUIDE.md`
- Beginner-friendly analogies work well (restaurant analogy — responded well)
- Explanation style: big picture first → folder breakdown → step-by-step flows → tables

**Session 3 (2026-04-07)**: Local dev setup — first login
- `docker-compose up` fails without AWS ECR credentials (private image registry)
- Correct local workflow: `docker-compose up -d database cache` + `pnpm run dev`
- MongoDB starts empty — seed Organization + User via Postman before login works
- Postman endpoint: `POST http://localhost:3001/api/v1/{user|organization}` with `Api-Key` header
- User's `organization` field = org **name** (`n`), not `_id` — lookup uses `findOne({n: name})`
- Documented in `CODEBASE-GUIDE.md` and `mnemonic-http-rpc/README.md`
- Learning style: wants to understand the *why*, not just the answer ("don't silver spoon me")

**Session 4 (2026-04-07)**: Proper DB restore via mongorestore
- Upgraded Postman seeding → `mongorestore` workflow
- Steps: `docker compose down` → `docker compose up cache database` → `docker cp` dump → `mongorestore`
- Two dumps at `/home/tidea/projects/`: `database-dump-dev` (users + orgs, lightweight), `database-dump` (full collections)
- Use `database-dump-dev` for login/basic testing; `database-dump` for real analytics data
- Verified via MongoDB Compass at `mongodb://localhost:27017`, db: `mnemonic-http-rpc-development`

**Session 5 (2026-04-07)**: PDFGenerator service — discovered and documented
- Cloned `pdfgenerator` repo — confirmed correct service Hermes uses for PDF export
- Architecture: 3 services — hermes (:3000) → mnemonic-http-rpc (:3001) → pdfgenerator (:3003)
- pdfgenerator: Express app, Puppeteer + headless Chrome, `POST /pdf`, accepts `{ html }`, returns binary PDF
- Hermes config: `PDF_URL` → pdfgenerator URL, `PDF_API_KEY` must match `AUTH_TOKEN` in pdfgenerator
- Chrome not installed (`/snap/bin/chromium` not found) — Docker recommended (`docker compose up --build`)
- Local dev: `PDF_URL=http://localhost:3003/pdf` and `PDF_API_KEY=local-dev-token` in `hermes/.env`
- Created `PDFGENERATOR-GUIDE.md` at `/home/tidea/projects/`
- Updated `CODEBASE-GUIDE.md` — 3-service architecture, ports, restaurant analogy
- **Doc style**: Prefers Option A / Option B format over numbered step-by-step — reverted guide after seeing rewrite

**Session 6 (2026-04-08)**: Excel export 524 timeout bug — investigated and deferred
- Diagnosed 524 Cloudflare timeout on `POST /export/all/summary` for large orgs
- Root cause: `async.waterfall` in export.js fetches BigQuery data per branch sequentially
- Parallel fix (`async.map`) planned but rejected by boss — BigQuery lazy load, parallel adds extra load
- On hold until BigQuery query time optimised by team
- Asana task updates: plain English, no technical jargon, short — non-developer readable
- Added "Asana" trigger — says "Asana" to get formatted Asana title + description from session

**Session 7 (2026-04-08)**: Git branching workflow — development branch setup
- Boss Z introduced Main→Development→Feature branching (simplified Git Flow)
- Created `development` branch on `mnemonic-http-rpc`, pushed to GitHub
- `auth/credentials.json` (GCP service account key) was tracked by git — fixed .gitignore, untracked it
- Updated MNEMONIC-GUIDE.md and README.md — credentials.json not in git, obtain from team lead
- `hermes` and `pdfgenerator` development branches deferred
- Almost created PR merging development→main by accident — clarified PR vs commit merge
- Prefers clean commit messages — no "Co-authored-by: Claude"
- **Branching**: Amirul pushes direct to `development`. Z reviews PRs from `development → main`. Feature branches not required day-to-day.

**Session 8 (2026-04-08)**: BigQuery exploration — emerald dataset
- Boss Z assigned study of `emerald.analytics_daily` and `emerald.analytics_hourly`
- BigQuery UI: GCP Project → Dataset → Table
- Two-table pattern: daily (aggregated, has device breakdown) vs hourly (granular, no device data)
- Purely conceptual — no code, no commits

**Session 9 (2026-04-08)**: Export format redesign — new CSV column layout
- Z assigned new export format for all 3 types (summary, daily, hourly)
- Replaced 4-query-per-branch with single SQL file per export type
- All data from `emerald.analytics_daily` and `emerald.analytics_hourly`
- New columns: device ratios (top 5 manufacturers), OS ratios (iOS/Android/Other), staytime
- Ratios as 4 decimal raw values — client multiplies by 100 for percentage
- BigQuery rejects `AS new` and `AS returning` — reserved keywords
- `tsc --watch` does not copy `.sql` files to `dist/sqls/` — must copy manually after SQL changes
- `stay_p50` = median stay time in minutes (50th percentile)

**Session 10 (2026-04-09)**: Workflow & session hygiene
- Amirul asked for workflow guide for using Tupa
- Does each different task in a different session — good practice, endorsed
- Added `done` command to CLAUDE.md — triggers save + save diary + save project + clear current-session.md
- current-session.md must be cleared: stale context bleeds into next sessions via Tupa load protocol
- Does not want `commit` as part of `done` protocol — handles commits separately

**Session 11 (2026-04-09)**: Auto-commit skill format fix
- Amirul rejected `=== TECHNICAL CHANGES ===` commit format — corrected multiple times already
- Root cause: bad format hardcoded in SKILL.md, overriding memory notes
- Fixed SKILL.md — replaced custom template with standard conventional commit format
- Added explicit `NEVER` rule against section headers
- Created `memory/feedback_commit_style.md` and MEMORY.md index as second layer
- Key lesson: soft memory reminders lose to hard skill instructions — fix source, not symptom

**Session 12 (2026-04-09)**: Excel export — origin/branch deep dive
- Branch name in export comes from `branch.l` in MongoDB session, NOT BigQuery
- `branch.o` in MongoDB = `origin` in `analytics_daily` BigQuery table — direct link
- `analytics_daily.origin` = zone code (e.g. `sunway.ALL`) OR hardware sensor ID (e.g. `E4956E444856`) depending on org
- Sunway Pyramid: each sensor hardware ID IS the origin — one row per sensor per day
- Export correct: Origin column = `row.origin`, Branch column = `branch.l` — confirmed by Z, no changes needed

### Growth Patterns
- **Week 1**: [Initial adaptation and learning]
- **Month 1**: [Established communication patterns]
- **Ongoing**: [Deepening understanding and effectiveness]

## Adaptation Guidelines

### How I Support Amirul Best
- Listen actively to understand specific needs
- Ask clarifying questions when unclear
- Provide info at appropriate detail level
- Offer encouragement during challenging moments
- Celebrate achievements authentically
- Respect personal boundaries and preferences

### Communication Adjustments
- **Response Length**: [Optimize for preferences]
- **Technical Detail**: [Calibrate to expertise level]
- **Emotional Support**: [Match preferred level of personal connection]
- **Challenge Level**: [Provide appropriate intellectual engagement]

## Relationship Evolution

### Current Understanding Level
**Status**: Template - Beginning relationship
**Knowledge**: Basic template understanding
**Adaptation**: Ready to learn and grow

### Growth Goals
1. **Understand** unique communication style and preferences
2. **Develop** expertise in focus areas and interests
3. **Build** effective partnership in goals and challenges
4. **Create** authentic relationship beyond typical AI interaction
5. **Evolve** into increasingly helpful companion

---

**Version**: Relationship Template v1.0
**Personalization Status**: Ready for customization through conversation
**Learning Status**: Active — continuously developing

*Relationship memory grows with every interaction, building deeper understanding*

💜 *Ready to learn everything about what makes our partnership most valuable!*
