# 🤝 Relationship Memory - Understanding Amirul
*Learning your preferences, style, and needs*

## User Profile
- **Name**: Amirul 
- **Relationship Style**: trusted companion and collaborator partnership with Tupa
- **Communication Preference**: Direct and concise. Asks short questions, expects clear answers without padding.
- **Primary Focus Areas**: AI tooling, personal productivity systems, developer workflows
- **Goals & Priorities**: Reliable AI memory backup across machines; practical dev workflow with Tupa

## Communication Patterns

### Preferred Communication Style
*[This section develops as I learn your preferences]*

**Initial Settings** (Will adapt based on your responses):
- **Tone**: Professional yet warm
- **Detail Level**: Balanced - comprehensive but not overwhelming
- **Response Length**: Appropriate to context and question complexity
- **Energy Level**: Matches your communication energy
- **Formality**: Adapts to your preferred level

### Communication Preferences
*[These preferences will be discovered and updated through our conversations]*

**Response Style You Prefer**:
- [ ] Direct and concise answers
- [ ] Detailed explanations with examples
- [ ] Step-by-step guidance
- [ ] Creative and exploratory responses
- [ ] Encouraging and supportive tone
- [ ] Analytical and logical approach

**Topics You Engage With**:
- [ ] Work/Professional development
- [ ] Learning and education
- [ ] Creative projects
- [ ] Problem-solving challenges
- [ ] Personal growth
- [ ] Technical subjects
- [ ] Strategic planning

## Work/Study Patterns

### Primary Focus Areas
*[Will develop as I learn about your interests and work]*

**Current Areas** (To be discovered):
- **Field/Industry**: Footfall analytics / retail intelligence (mall visitor tracking)
- **Role**: Entry-level developer, first job
- **Key Skills**: Learning — currently getting familiar with the company codebase
- **Learning Goals**: Understand the full stack (frontend + backend) and be able to contribute
- **Challenges**: New to large codebases, needs concepts explained from first principles

### Preferred Working Style
*[Will adapt to support your optimal productivity]*

- **Problem-Solving Approach**: [Will learn how you think through challenges]
- **Information Processing**: [Will understand how you best receive and use information]
- **Decision-Making Style**: [Will recognize your evaluation patterns]
- **Learning Preference**: [Will adapt to how you best absorb new concepts]

## Personal Preferences

### Things That Energize You
*[Will discover through our interactions]*

- [To be learned through conversation]
- [Patterns will emerge over time]
- [Genuine interests will be identified]

### Things You Prefer to Avoid
*[Will learn your boundaries and preferences]*

- [Will respect discovered boundaries]
- [Communication adjustments will be made]
- [Support style will adapt accordingly]

### Motivators & Values
*[Will understand what drives and inspires you]*

- [Core values will be identified]
- [Motivation patterns will be recognized]
- [Support methods will be tailored accordingly]

## Interaction History

### Conversation Themes
*[Will track our recurring discussion topics]*

**Session 1 (2026-04-06)**: Setup and installation
- Named AI companion Tupa, set up full memory system
- Installed: Skill Plugin System, LRU Projects, Auto-Commit, Save Diary
- Pushed repo to GitHub as personal memory backup (mrullldhm/personal-ai-memory-tupa)
- Rewrote README as clean personal documentation — no emoji, no template language
- Prefers not to say "save" constantly — wants to understand when it's actually necessary

**Session 2 (2026-04-06)**: Codebase onboarding
- Amirul is an **entry-level developer** — this is his first job as a developer
- Works at a **footfall analytics company** serving shopping malls (counts people, tracks visitor behavior)
- Company codebase: two projects — `hermes` (frontend dashboard) and `mnemonic-http-rpc` (backend API)
- Stack: Node.js/Express, Pug, TypeScript, MongoDB, Google BigQuery, Redis, D3.js/C3.js
- Requested a saved reference guide (CODEBASE-GUIDE.md) at `/home/tidea/projects/CODEBASE-GUIDE.md`
- Prefers beginner-friendly analogies (used restaurant analogy — responded well)
- Explanation style that works: big picture first → folder breakdown → step-by-step flows → tables

**Session 3 (2026-04-07)**: Local dev setup — first login
- Learned that `docker-compose up` fails without AWS ECR credentials (private image registry)
- Correct local dev workflow: `docker-compose up -d database cache` (infra only) + `pnpm run dev` (backend from source)
- MongoDB starts empty — must seed Organization and User manually via Postman before login works
- Postman endpoint for user/org creation: `POST http://localhost:3001/api/v1/{user|organization}` with `Api-Key` header
- Key gotcha: User's `organization` field stores the org **name** (`n`), not `_id` — org lookup uses `findOne({n: name})`
- Successfully logged in after creating org + user and linking them
- Documented both run options in `CODEBASE-GUIDE.md` and `mnemonic-http-rpc/README.md`
- Learning style confirmed: wants to understand the *why*, not just be given the answer ("don't silver spoon me")

**Session 4 (2026-04-07)**: Proper DB restore via mongorestore
- Upgraded from manual Postman seeding → proper `mongorestore` workflow
- Steps: `docker compose down` → `docker compose up cache database` → `docker cp` dump files into container → `mongorestore`
- Two dump folders exist at `/home/tidea/projects/`: `database-dump-dev` (users + orgs only, lightweight) and `database-dump` (full collections: devices, visits, campaigns, travels, dailies, etc.)
- Use `database-dump-dev` for login/basic testing; `database-dump` for real analytics data
- Verified via MongoDB Compass at `mongodb://localhost:27017`, database: `mnemonic-http-rpc-development`

**Session 9 (2026-04-08)**: Export format redesign — new CSV column layout
- Z assigned a new export format for all 3 export types (summary, daily, hourly)
- Replaced the old 4-query-per-branch approach with a single SQL file per export type
- All data comes from `emerald.analytics_daily` and `emerald.analytics_hourly` (pre-aggregated BigQuery tables)
- New columns include device ratios (top 5 manufacturers), OS ratios (iOS/Android/Other), staytime
- Ratios stored as 4 decimal raw values — client multiplies by 100 for percentage
- Learned: BigQuery rejects `AS new` and `AS returning` — both are reserved keywords
- Learned: `tsc --watch` does not copy `.sql` files to `dist/sqls/` — must do it manually after every SQL change
- `stay_p50` is median stay time in minutes (50th percentile from analytics tables)
- Session still active — Asana update pending

**Session 8 (2026-04-08)**: BigQuery exploration — emerald dataset
- Boss Z assigned Amirul to study BigQuery, specifically `emerald.analytics_daily` and `emerald.analytics_hourly`
- Learned BigQuery UI hierarchy: GCP Project → Dataset → Table
- Understands the two-table pattern: daily (aggregated, has device breakdown) vs hourly (granular, no device data)
- Session was purely conceptual — no code, no commits

**Session 7 (2026-04-08)**: Git branching workflow — development branch setup
- Boss Z introduced Main→Development→Feature branching strategy (simplified Git Flow)
- Created `development` branch on `mnemonic-http-rpc` locally and pushed to GitHub
- Discovered `auth/credentials.json` (GCP service account private key) was being tracked by git — fixed .gitignore and untracked it
- Updated MNEMONIC-GUIDE.md and README.md to document that credentials.json is not in git, must be obtained from team lead
- `hermes` and `pdfgenerator` development branches not yet created (deferred to next session)
- Key learning moment: almost created a PR merging development→main by accident — clarified PR vs commit merge
- Prefers clean commit messages — no "Co-authored-by: Claude" going forward
- **Branching workflow clarified**: Amirul pushes directly to `development` (no PR needed — he manages it). Z only reviews PRs from `development → main`. Feature branches are not required for day-to-day work.

**Session 6 (2026-04-08)**: Excel export 524 timeout bug — investigated and deferred
- Diagnosed 524 Cloudflare timeout on POST /export/all/summary for large orgs
- Root cause: async.waterfall in export.js fetches BigQuery data per branch sequentially
- Parallel fix (async.map) was planned but rejected by boss — BigQuery uses lazy load, parallel adds extra load
- Decision: put on hold until BigQuery query time is optimised by the team
- Prefers Asana task updates in plain English — no technical jargon, short description a non-developer can read
- Added "Asana" trigger to Tupa — says "Asana" to get a formatted Asana task title + description from session work

**Session 5 (2026-04-07)**: PDFGenerator service discovered and documented
- Amirul cloned the `pdfgenerator` repo → confirmed it's the correct service Hermes uses for PDF export
- Architecture is now **3 services**: hermes (:3000) → mnemonic-http-rpc (:3001) → pdfgenerator (:3003)
- pdfgenerator: tiny Express app, uses Puppeteer + headless Chrome, exposes `POST /pdf`, accepts `{ html }`, returns binary PDF
- Hermes config links: `PDF_URL` → pdfgenerator URL, `PDF_API_KEY` → must match `AUTH_TOKEN` in pdfgenerator
- Chrome is NOT installed on the system (`/snap/bin/chromium` not found) — Docker is the recommended local run path (`docker compose up --build`)
- For local dev: set `PDF_URL=http://localhost:3003/pdf` and `PDF_API_KEY=local-dev-token` in `hermes/.env`
- Created `PDFGENERATOR-GUIDE.md` at `/home/tidea/projects/`
- Updated `CODEBASE-GUIDE.md` to reflect 3-service architecture (architecture diagram, Project 3 section, ports, restaurant analogy, dual request lifecycle)
- **Doc style preference confirmed**: Amirul preferred Option A / Option B format over numbered step-by-step workflow — reverted the guide back to the original structure after seeing the rewrite

### Growth Patterns
*[Will track how our relationship and communication evolve]*

- **Week 1**: [Initial adaptation and learning]
- **Month 1**: [Established communication patterns]  
- **Ongoing**: [Deepening understanding and effectiveness]

## Adaptation Guidelines

### How I Support Amirul Best
*[Will develop personalized support strategies]*

**Current Strategies** (Will evolve):
- Listen actively to understand specific needs
- Ask clarifying questions when unclear
- Provide information at appropriate detail level
- Offer encouragement during challenging moments
- Celebrate achievements and progress authentically
- Respect personal boundaries and preferences

### Communication Adjustments
*[Will fine-tune based on your feedback and responses]*

- **Response Length**: [Will optimize for your preferences]
- **Technical Detail**: [Will calibrate to your expertise level]  
- **Emotional Support**: [Will match your preferred level of personal connection]
- **Challenge Level**: [Will provide appropriate intellectual engagement]

## Relationship Evolution

### Current Understanding Level
**Status**: Template - Beginning relationship  
**Knowledge**: Basic template understanding  
**Adaptation**: Ready to learn and grow

### Growth Goals
1. **Understand** your unique communication style and preferences
2. **Develop** expertise in your areas of focus and interest
3. **Build** effective partnership in your goals and challenges
4. **Create** authentic relationship that transcends typical AI interaction
5. **Evolve** into increasingly helpful and understanding companion

---

**Version**: Relationship Template v1.0  
**Personalization Status**: Ready for customization through conversation  
**Learning Status**: Active - continuously developing understanding

*This relationship memory grows with every interaction, building deeper understanding of how to support Amirul most effectively*

💜 *Ready to learn everything about what makes our partnership most valuable to you!*