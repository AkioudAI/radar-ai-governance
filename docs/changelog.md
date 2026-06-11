# Changelog

> Public version history for transparency and anteriority.

---

## v0.1.0-alpha.1 — June 2026

- **Versioning restarted**: semver adopted — replaces internal sequential numbering (v3.20→v3.40)
- **Pre-commercial phase**: `0.x` signals pre-1.0 maturity
- **INPI Soleau deposit**: DSO2026021562 (€15, 5 years) — anteriority proof locked
- **Public reference repo**: AkioudAI/radar-ai-governance — 7 docs, 6 screenshots

*Transition documented June 11, 2026. See VERSIONING.md for the full roadmap.*

---

## v3.40 — June 2026 (last internal version)

### Dashboard
- Complete design system refactoring — neutral palette, design tokens, dark/light mode
- Loading skeletons on all 11 pages (CardSkeleton, TableSkeleton, ChartSkeleton)
- Command palette (⌘K global search)
- Notification bell with merged alerts + notifications feed
- Conformity assessment page — gap analysis against EU AI Act
- Regulatory updates live feed on Compliance page
- Digest email preview in Settings

### Backend
- Notification center with SQLite persistence
- Dashboard API optimized — DB-level queries instead of full-table scans
- SSE stream efficiency — poll interval reduced for multi-client scenarios
- Alert deduplication by source + agent
- PII validators cleanup — removed dead duplicate implementations
- License validation hardening — InvalidSig fallback

---

## v3.38 — May 2026

### Dashboard
- Evidence packs operator surface (admin RBAC)
- Kill Switch theater with confirmation modals
- Trial signups management with conversion workflow
- Settings page (users, API keys, SSO, SIEM, sessions)

### Backend
- Trial → paid license conversion pipeline (Stripe webhook)
- SIEM delivery engine (CEF format, syslog)
- Email digest scheduler (DripScheduler)
- Governance evidence pack registry
- Article 14 (EU AI Act) + Article 35 (GDPR) DPIA evidence generators

---

## v3.35 — April 2026

### Dashboard
- DataTable component (sortable, expandable, CSV export)
- ScoreChart + BreakdownChart + TrendSparkline
- Enhanced StatCards with sparklines and colorStatus
- Responsive sidebar with collapsible sections
- Empty states with guided CTAs on all pages

### Backend
- Regulatory update checker with hot-reload
- Conformity assessment generator
- Model cards extractor (healthcare profile)
- Content safety scanner (prompt injection, jailbreak detection)

---

## v3.20 — March 2026

### Core
- Initial public release
- Agent SDK (Python) — instrumented LLM wrapper
- PII scanner — 40 detection patterns
- Compliance scorer — EU AI Act initial support
- Audit trail — Merkle chain integrity
- CISO dashboard — initial release
- Trial license system (30-day, auto-generated)

---

## Prior History

RADAR builds on AKIOUD AI's open-source AI governance research and development.

### Key Milestones
- **April 2024**: AKIOUD AI incorporated (SIREN 924 929 730, INPI/RNE)
- **September 2024**: First PII detection patterns — foundation of the detection engine
- **October 2025**: [akios](https://github.com/akios-ai/akios) — open-source security cage for multi-agent AI (GPL 3.0). Kernel sandboxing (seccomp-bpf), 44 PII patterns, workflow orchestration. 65 commits.
- **February 2026**: [EnforceCore](https://github.com/akios-ai/EnforceCore) — open-source runtime enforcement library (Apache 2.0). PII masking, policy checks, Merkle audit as a decorator. 127 commits, 24 releases. Extracted from akios as a standalone library.
- **March 2026**: RADAR v3.20 public release — CISO dashboard, PII scanner (40 patterns), compliance scorer, Merkle audit trail
- **June 2026**: RADAR v3.40 — design system, conformity assessment, notification center, 212 tests (207 passing)

All dates verifiable via GitHub repository creation timestamps and INPI registration data.
