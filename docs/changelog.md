# Changelog

> Public version history for transparency and anteriority.

---

## v3.40 — June 2026

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

RADAR builds on AKIOUD AI's open-source AI governance research and development, which began in 2024.

### Key Milestones
- **April 2024**: AKIOUD AI incorporated (SIREN 924 929 730, INPI/RNE)
- **September 2024**: First PII detection patterns — foundation of the detection engine
- **October 2024**: [EnforceCore](https://github.com/akios-ai/EnforceCore) — open-source runtime enforcement library (Apache 2.0). PII masking, policy checks, Merkle audit as a decorator. 127 commits, 32 releases.
- **January 2025**: [akios](https://github.com/akios-ai/akios) — open-source security cage for multi-agent AI (GPL 3.0). Kernel sandboxing (seccomp-bpf), 44 PII patterns, workflow orchestration. 65 commits, 32 releases. Built on EnforceCore.
- **January 2025**: Merkle audit chain design finalized, compliance scoring engine v1
- **July 2025**: CISO dashboard MVP
- **March 2026**: v3.20 public release
- **June 2026**: v3.40 — design system, conformity, notifications, test coverage
