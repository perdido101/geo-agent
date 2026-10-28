# OrbitGEO — autonomous GEO / AEO intelligence

GEO Agent is a deployable, no-framework MVP combining a GitHub Pages-compatible dashboard with a separately hosted Node 22+ API. It audits public websites, samples supported AI answer engines, creates prioritized GEO tasks, generates genuinely useful content briefs, and can **create approved WordPress drafts** with temporary credentials. Billing is deliberately deferred.

## Product areas
- **Overview** — real audit activity and sampled mention rates, no fictional metrics.
- **Website Health** — live HTTPS fetch, crawler permissions, sitemap, llms.txt, JSON-LD, FAQ, metadata, canonical, indexability and answer-ready content.
- **AI Answers** — OpenAI with web search, Gemini with Google grounding, Perplexity Sonar (when separately configured), with the actual returned text and citations saved.
- **Opportunities** — actionable prioritized tasks, with audit evidence, approvals and history.
- **Action Studio** — generate an evidence-based content draft (AI optional), approve it and publish as a **WordPress draft** through an explicit user action. No automatic public posting.
- **Projects & Settings** — project switching, frontend API connection, single-operator development auth.
- **MAPROUTE reference checklist** — the model covers MAPROUTE's published GEO implementation, but does not import its owner-only analytics or edit the site.

## Local development
```bash
node --version # >= 22 recommended
npm run dev
# open http://localhost:8787
npm test
```
No packages required. When starting locally, the API is on the same origin as the UI. The first project can be your own website, e.g. https://maproute.app.

### Optional environment variables
```
PORT=8787
API_TOKEN=replace-with-a-long-private-token
ALLOWED_ORIGIN=https://perdido101.github.io
OPENAI_API_KEY=
GEMINI_API_KEY=
PERPLEXITY_API_KEY=
```
AI provider testing requires paid provider keys and an independently hosted backend. Provider API models and search/grounding availability can change. Failures are surfaced; results are never invented.

## Publish the static frontend to GitHub Pages
1. Go to repo **Settings → Pages**.
2. Select **Deploy from a branch** → **main** → **/docs** → Save.
3. The site is expected at https://perdido101.github.io/geo-agent/ only after GitHub reports a successful Pages deployment.
4. In the app's **Settings**, enter the deployed backend's HTTPS origin and development API token.

GitHub Pages is **static only**. Website audits, API keys, ongoing agent jobs, persistent data and WordPress drafts require running `server/index.js` on a Node host with persistent storage and HTTPS. Do not put provider keys or WordPress credentials in GitHub Pages or the repo.

## API
- `GET /api/health` provider availability
- `GET /api/state` projects, audits, observations, tasks, drafts
- `POST /api/projects` add public HTTPS website
- `POST /api/projects/:id/audit` run technical GEO/AEO audit
- `POST /api/projects/:id/query` observe answer from a configured provider
- `POST /api/projects/:id/brief` create an evidence-backed draft proposal
- `POST /api/actions/:id` change review status
- `POST /api/drafts/:id/wordpress` create **draft**, requiring explicit request and temporary WordPress application password

## Reliability and privacy limitations
This is a **single-operator alpha**, NOT a public multi-tenant paid SaaS. Local JSON storage and bearer-token access must be replaced with a real database, tenant-scoped authentication, queues, quotas, and site-ownership verification before onboarding customers. There is no automated public publishing, no claim of changing AI recommendations, and no evidence that a particular optimization caused an observed visibility change.

The public-domain-only fetcher checks DNS/IP to reduce SSRF risk, rejects redirects and non-HTTPS URLs; production hosting still requires network-level egress protection and DNS pinning. Explicit WordPress credentials are supplied transiently for one action; they are never stored. Rate limits and cost controls are needed before offering unrestricted API access.

`llms.txt` is an optional AI-facing convention, not an established guarantee of ranking. JSON-LD must accurately describe visible content. Robots directives and AI crawler access influence eligibility but do not guarantee inclusion in any AI answer.

## Next engineering milestones
Production database + row-level tenant authorization; verified website ownership; scheduled queue and retention; provider usage metering; WordPress OAuth or secure credentials vault; richer citation/competitive analysis; real Search Console and analytics connectors; Stripe integration; observability, backups, accessibility and security review.
