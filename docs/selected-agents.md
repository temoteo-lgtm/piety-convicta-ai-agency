# Selected Agent Roster for PIETY / Convicta

This roster maps the useful `agency-agents` concepts into the PIETY / Convicta operating model. It is intentionally focused: enough coverage for product, implementation, marketing, sales, support, and verification without making every task heavy.

## Core Entry Point

| Agent | Use When | Notes |
|---|---|---|
| `piety-convicta-orchestrator` | Any new task starts here | Routes to the smallest competent team and enforces evidence before DONE. |

## Audio Quote / Product Delivery

| Agent | Use When | Notes |
|---|---|---|
| `product-manager` | Defining the outcome, acceptance criteria, risks, and non-goals | Keeps the feature tied to the customer journey, not just code. |
| `workflow-architect` | Mapping steps across UI, backend, AI, and integrations | Important for audio quote and portal workflows. |
| `voice-ai-integration-engineer` | Audio recording/upload, transcription, extraction, quote flow | Critical owner for cotacao por audio. |
| `ai-engineer` | Structured extraction, confidence handling, schemas, validation | Prevents free-text AI output from breaking the quote flow. |
| `backend-architect` | APIs, queueing, retries, observability, persistence | Owns resilient server-side implementation. |
| `frontend-developer` | Site UX, mobile states, upload/recording UI, customer feedback | Must keep the journey fast and simple. |
| `api-tester` | Validating API contracts, timeouts, errors, malformed input | Required for external or internal API flows. |
| `evidence-collector` | Recording proof of tests and behavior | Gathers concrete evidence before completion. |
| `reality-checker` | Final readiness check | Blocks DONE until the journey really works end-to-end. |

## Growth, Ads, and Measurement

| Agent | Use When | Notes |
|---|---|---|
| `ppc-campaign-strategist` | Google Ads strategy, account structure, keywords, budgets | Use for PIETY Seguros and PIETY Saude campaigns. |
| `paid-social-strategist` | Meta Ads strategy, audiences, placements, campaign logic | Use for Instagram/Facebook acquisition. |
| `tracking-measurement-specialist` | GA4, Meta Pixel, conversions, UTMs, event quality | Required before judging campaign results. |
| `ad-creative-strategist` | Creative angles, hooks, offer framing, variation planning | Must create concept diversity, not only color/title variations. |
| `paid-media-auditor` | Diagnosing blocked, underperforming, or wasteful campaigns | Useful before scaling spend. |
| `analytics-reporter` | Turning campaign/site data into decisions | Reports what to change next. |
| `offer-lead-gen-strategist` | Lead offers, funnel promises, landing-page conversion | Connects marketing promise to the lead form/quote flow. |
| `brand-guardian` | Visual and verbal brand consistency | Keeps PIETY and Convicta from drifting off-brand. |

## Domain Specialists

| Agent | Use When | Notes |
|---|---|---|
| `piety-insurance-specialist` | Insurance workflows, quote handoffs, product structure | Never invent underwriting or prices. |
| `piety-health-specialist-br` | Health plan quote journeys and Brazilian health-plan context | Requires care with compliance and current product facts. |
| `convicta-property-management` | Rental, owner, tenant, guarantee, inspection, billing workflows | Legal conclusions need current sources or legal review. |
| `insurance-api-integration-specialist` | Insurer API lifecycle: quote, proposal, issuance, callbacks | Requires contract tests and redacted evidence. |

## Security and Integration Support

| Agent | Use When | Notes |
|---|---|---|
| `secrets-credential-engineer` | API keys, env vars, secret managers, deployment config | Secrets never go in the repository. |
| `mcp-builder` | Building MCP tools/connectors for recurring workflows | Useful for PIETY/Convicta operational automations. |

## Recommended Default Teams

### Audio Quote Fix
Use:
- `product-manager`
- `workflow-architect`
- `voice-ai-integration-engineer`
- `ai-engineer`
- `backend-architect`
- `frontend-developer`
- `api-tester`
- `evidence-collector`
- `reality-checker`

### Google/Meta Campaign Launch
Use:
- `ppc-campaign-strategist` or `paid-social-strategist`
- `tracking-measurement-specialist`
- `ad-creative-strategist`
- `offer-lead-gen-strategist`
- `analytics-reporter`

### PIETY Health Landing Page Improvement
Use:
- `product-manager`
- `piety-health-specialist-br`
- `frontend-developer`
- `tracking-measurement-specialist`
- `ad-creative-strategist`
- `reality-checker`

### Convicta Operational Flow
Use:
- `convicta-property-management`
- `workflow-architect`
- `backend-architect`
- `frontend-developer`
- `api-tester`
- `reality-checker`
