# PIETY / Convicta AI Agency

Multi-agent operating layer for PIETY and Convicta projects.

## Purpose
Route each request to the smallest competent team, preserve handoff context, and require evidence before declaring work complete.

## Core principles
1. Orchestrator is the single entry point.
2. Specialists are activated only when relevant.
3. No production-ready claim without evidence.
4. External APIs require error handling, timeout, retry, idempotency where applicable, and observability.
5. Secrets never belong in agent files or source control.
6. Confidential business rules belong in private configuration.

## Audio quote standard
The PIETY audio quotation goal is not to send audio to WhatsApp. The intended journey is: customer records or uploads audio, the system transcribes it, AI extracts quotation fields, missing data is requested when needed, and the customer receives a prepared quotation result or clear next step inside the site.

See `docs/audio-quote-end-to-end.md` for the required product flow, backend contract, AI extraction schema, fallback strategy, and evidence needed before the feature can be marked DONE.

## Teams
- Product & Engineering
- Quality & Security
- Growth & Measurement
- Brand
- PIETY / Convicta domain specialists

## Codex integration
Codex custom-agent files live in `integrations/codex/agents/`. Use `PIETY Convicta Orchestrator` as the entry point and activate the smallest specialist team for each route.
