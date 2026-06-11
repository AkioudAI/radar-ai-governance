# Regulatory Coverage

> RADAR monitors AI agents against the following regulations.
> Coverage expands as new regulations are enacted.

---

## Active Regulations

### EU AI Act (Regulation 2024/1689)

| Article | Title | RADAR Evidence |
|---------|-------|---------------|
| Art 9 | Risk Management System | Risk flag detection, continuous risk scoring |
| Art 13 | Transparency & Provision of Information | End-user disclosure tracking, transparency indicators |
| Art 14 | Human Oversight | Human-in-the-loop markers, override log auditing |
| Art 16 | Technical Documentation | Auto-generated technical docs from audit events |
| Art 17 | Quality Management System | Per-agent quality scoring, policy compliance rate |
| Art 26 | Obligations of Deployers | Usage monitoring, boundary enforcement |

**Compliance Score**: 0–100 per agent, article-level breakdown, remediation guidance.

---

### GDPR (Regulation 2016/679)

| Article | Title | RADAR Evidence |
|---------|-------|---------------|
| Art 5 | Principles (data minimization) | PII detection volume tracking, minimization indicators |
| Art 25 | Data Protection by Design | Policy enforcement rules, PII redaction evidence |
| Art 30 | Records of Processing | Automated processing activity log from audit events |
| Art 35 | Data Protection Impact Assessment (DPIA) | Auto-generated DPIA evidence pack |

---

### Sector-Specific

RADAR includes sector-specific profiles for:
- **Healthcare** — HIPAA alignment, medical device software provisions
- **Finance** — DORA (Digital Operational Resilience Act) readiness

---

## Regulatory Update Pipeline

RADAR automatically tracks regulation versions from official sources:
- Checks daily for updates to EU AI Act and GDPR article definitions
- Compares installed vs. latest version
- Surfaces changes with severity (critical, major, minor, informational)
- Hot-reload article weights without restart

The pipeline status is visible from the Dashboard → Compliance page.

---

## Roadmap

| Regulation | Status |
|-----------|--------|
| EU AI Act | Active |
| GDPR | Active |
| NIST AI RMF 1.0 | Q3 2026 |
| ISO/IEC 42001:2023 | Q3 2026 |
| DORA (EU 2022/2554) | Q4 2026 |
| California AI Bill (SB-1047) | Monitoring |
| UK AI Regulation Bill | Monitoring |
