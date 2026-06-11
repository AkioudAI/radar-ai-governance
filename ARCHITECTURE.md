# RADAR — System Architecture

> High-level architecture overview. Implementation details remain proprietary.
> RADAR evolves AKIOUD AI's open-source stack: [akios](https://github.com/akios-ai/akios) (GPL 3.0, Oct 2025) + [EnforceCore](https://github.com/akios-ai/EnforceCore) (Apache 2.0, Feb 2026).

---

## Deployment Model

RADAR ships as a **single Docker container** containing:
- Python 3.11 FastAPI server (REST API + middleware)
- React SPA dashboard (served as static files)
- Embedded SQLite audit database (SQLite 3.x)

```
                    ┌──────────────────┐
                    │   Docker Host     │
                    │                  │
  Port 8080 ◄───────┤  radar:3.40.4   │
                    │                  │
                    │  /data           │
                    │  ├── audit.db    │
                    │  ├── license     │
                    │  └── exports/    │
                    └──────────────────┘
```

---

## Component Stack

### Data Plane (SDK → Server)

```
Agent SDK (Python)
    │  instrumented LLM calls
    ▼
RADAR Server (FastAPI)
    ├── PII Scanner     40+ regex + validation patterns
    ├── Policy Enforcer  Prompt injection, jailbreak, content rules
    ├── Compliance       Article-by-article evidence scoring
    └── Audit Store      Merkle-chained, optionally encrypted
```

### Control Plane (Dashboard)

```
Browser ── REST/SSE ──► FastAPI
                          ├── Dashboard API   Overview + agents + events
                          ├── Alerts API      Open/acknowledged/resolved
                          ├── Compliance API  Scores per regulation/article
                          ├── Governance API  Evidence packs (DPIA, Art 14)
                          ├── Settings API    Users, API keys, SSO, SIEM
                          └── SSE Stream      Live event feed for dashboard
```

### Security

```
Request ──► CORSMiddleware
          ──► AuthMiddleware      JWT session or API key
          ──► RBAC                 admin | operator | viewer
          ──► RateLimitMiddleware  Per-IP, configurable
          ──► LicenseMiddleware    Tier enforcement
          ──► Route Handler
```

---

## Data Model

### Core Entities

| Entity | Storage | Description |
|--------|---------|-------------|
| AuditEvent | SQLite `audit_events` | Every LLM call — prompt, response, agent, timestamp |
| PII Detection | JSON field on event | Type (IBAN, CPR, email...), value (redacted), confidence |
| Policy Violation | JSON field on event | Rule ID, severity, matched content |
| Agent Summary | In-memory / derived | Aggregated from events — count, score, PII rate |
| License | JSON file on disk | Tier, expiry, features, RSA signature |
| Kill Switch Flag | File on disk | Atomic file-based state machine |
| User / API Key | SQLite `auth.db` | PBKDF2 hashed passwords, SHA-256 hashed API keys |

### Audit Trail Integrity

Each event is Merkle-chained:
```
Event N-1  ──► Event N  ──► Event N+1
prev_hash    prev_hash    prev_hash  = SHA-256(event || prev_hash)
```
The Merkle root is verifiable at any time. Tampering with any event breaks the chain.

---

## PII Detection

### Pattern Categories

| Category | Examples | Count |
|----------|----------|-------|
| EU National IDs | CPR (DK), BSN (NL), PESEL (PL), NIF (ES), Personnummer (SE) | 8 |
| Financial | IBAN, credit card (Luhn), SWIFT/BIC | 3 |
| Healthcare | NPI (US), NHS number (UK), health insurance IDs | 4 |
| Biometric | Fingerprint template IDs, facial recognition vectors | 2 |
| Legal / Extended | Passport numbers, social security, tax IDs | 23+ |

### Validation

Each pattern includes a validator function (e.g., Luhn for credit cards, MOD97 for IBAN, weighted checksums for national IDs). Detections without validator matches are flagged as lower confidence.

---

## Compliance Scoring

The scoring engine evaluates every agent event against regulatory articles:

1. **Evidence gathering** — For each article, collect evidence from events (transparency indicators, human oversight markers, risk flags)
2. **Weighted scoring** — Each evidence item has a weight; unsatisfied items reduce the score
3. **Critical failure cap** — Missing high-weight evidence caps the article score at 30%
4. **Agent correlation** — Scores are per-agent and aggregated for the overall compliance picture

### Scoring output includes:
- Overall score (0–100)
- Per-article breakdown
- Remediation recommendations
- Trend data (30-day history)

---

## Scale & Performance

| Metric | Trial | Team | Enterprise |
|--------|-------|------|------------|
| Max events/day | 50 | 5,000 | Unlimited |
| Max agents | — | 50 | Unlimited |
| PII patterns | 40 | 40 | 40 |
| Dashboard latency | <200ms | <200ms | <200ms |
| Audit DB size | SQLite | SQLite | SQLite + WAL |

The embedded SQLite database handles up to ~100K events comfortably. For higher volumes, an external SQLite configuration with WAL mode and separate volume mount is recommended.

---

## Compliance & Standards

RADAR is designed for:
- **EU AI Act** Article compliance scoring and evidence generation
- **GDPR** DPIA automation (Article 35)
- **ISO/IEC 42001:2023** AI management system alignment
- **NIST AI RMF** framework mapping (planned)
- **SOC 2** audit trail with cryptographic integrity

The platform itself runs on-premise with zero outbound data transmission (no telemetry, no cloud dependency).
