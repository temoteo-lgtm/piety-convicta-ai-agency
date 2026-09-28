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

## Teams
- Product & Engineering
- Quality & Security
- Growth & Measurement
- Brand
- PIETY / Convicta domain specialists
