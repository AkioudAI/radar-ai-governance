# RADAR — AI Governance & Compliance Platform

> **Published**: 11 June 2026 — Public reference repository
> **Owner**: AKIOUD AI SAS — SIREN 924 929 730 — 8 B Rue Abel, 75012 Paris

**Continuous compliance monitoring for AI agents and LLM systems.**

RADAR is the commercial evolution of AKIOUD AI's open-source AI governance stack — building on [akios](https://github.com/akios-ai/akios) (GPL 3.0, security cage for agents) and [EnforceCore](https://github.com/akios-ai/EnforceCore) (Apache 2.0, runtime enforcement).

RADAR is a self-hosted, zero-cloud platform that monitors AI agents in real-time, scores them against regulations (EU AI Act, GDPR), detects PII leaks, enforces policies, and produces regulator-ready evidence packs — all from your own infrastructure.

---

## What RADAR Does

| Capability | Description |
|-----------|-------------|
| **Agent Monitoring** | Track every LLM call, prompt, and response across agents |
| **PII Detection** | 40+ patterns — national IDs, healthcare, financial, biometric |
| **Compliance Scoring** | Real-time EU AI Act & GDPR article-by-article scores |
| **Policy Enforcement** | Detect prompt injection, jailbreaks, content violations |
| **Audit Trail** | Cryptographically verifiable Merkle chain — tamper-proof |
| **Evidence Packs** | DPIA, Article 14, Article 16 — regulator-ready exports |
| **Kill Switch** | Emergency agent shutdown with confirmation workflow |
| **CISO Dashboard** | Real-time overview with dark/light mode, charts, SSE live feed |

---

## Architecture

RADAR is a single-binary deployment (Python + React) with an embedded SQLite audit database. No external cloud dependency — everything runs on-premise or in your VPC.

```
┌─────────────────────────────────────────────────┐
│                   CISO Dashboard                │
│              (React SPA, dark/light)            │
├─────────────────────────────────────────────────┤
│                  REST API                       │
│         FastAPI — auth, RBAC, SSE               │
├──────────┬──────────┬──────────┬────────────────┤
│ PII      │ Policy   │Compliance│ Audit Trail    │
│ Scanner  │ Enforcer │ Scorer   │ Merkle Chain   │
├──────────┴──────────┴──────────┴────────────────┤
│              SQLite Audit DB                    │
│       (encrypted at rest if configured)         │
└─────────────────────────────────────────────────┘
```

See [ARCHITECTURE.md](ARCHITECTURE.md) for the full system design.

---

## Project Lineage

RADAR is built on research and open-source work by AKIOUD AI since 2024:

| Project | Type | License | Description |
|---------|------|---------|-------------|
| [**akios**](https://github.com/akios-ai/akios) | Open-source | GPL 3.0 | Security cage for multi-agent AI — kernel sandboxing, 44 PII patterns, workflow orchestration. 65 commits, 32 releases. Created Oct 2025. |
| [**EnforceCore**](https://github.com/akios-ai/EnforceCore) | Open-source | Apache 2.0 | Runtime enforcement library — PII masking, policy checks, Merkle audit as a decorator. 127 commits, 24 releases. Extracted Feb 2026. |
| **RADAR** | Commercial | Proprietary | CISO dashboard, compliance scoring, evidence packs, regulatory pipeline |

The same core technology — PII detection engine, Merkle audit chain, policy enforcement — evolved from open-source libraries into a complete compliance platform. This repository documents RADAR's architecture, features, and development history.

---

## Regulations Covered

- **EU AI Act** — Articles 9, 10, 11, 12, 13, 14, 15, 26, 61 — scoring + evidence generation
- **GDPR** — Articles 5, 6, 17, 22, 25, 30, 32, 33, 35 — DPIA automation, data protection
- **ISO 42001** — AI management system alignment
- Regulatory update pipeline — automatic version checks with change diff

---

## Deployment

Single Docker Compose command:

```bash
docker compose up -d
```

RADAR runs on port 8080 with:
- Embedded SQLite database (no external DB needed)
- Optional encryption at rest for audit events
- JWT-based auth with SSO (OIDC, SAML) support
- RBAC roles: admin, operator, viewer

---

## Features by Tier

### Trial (30 days, free)
- 1 regulation (EU AI Act)
- 50 events/day
- Dashboard + basic compliance scoring

### Team
- 2 regulations (EU AI Act + GDPR)
- 5,000 events/day
- Evidence packs, policy enforcement, alerts

### Enterprise
- All regulations + regulatory update pipeline
- Unlimited events
- SIEM/Splunk forwarding, SSO, DMA (scenarios engine)
- Dedicated support

---

## Company

RADAR is built by **AKIOUD AI**, a French AI governance company.

- **Legal form**: SAS, société par actions simplifiée
- **SIREN**: 924 929 730
- **SIRET**: 924 929 730 00019
- **TVA**: FR24 924 929 730
- **Address**: 8 B Rue Abel, 75012 Paris, France
- **Incorporated**: 1 April 2024 — Registre National des Entreprises (INPI)
- **NAF/APE**: 62.01Z — Programmation informatique
- **Website**: https://www.akioud.ai
- **Contact**: team@akioud.ai

---

## License

This repository is provided for reference and transparency. The RADAR source code is proprietary. See [LICENSE](LICENSE) for details.

© 2024–2026 AKIOUD AI. All rights reserved.
