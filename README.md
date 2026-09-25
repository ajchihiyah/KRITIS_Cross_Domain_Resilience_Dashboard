<img width="1287" height="943" alt="image" src="https://github.com/user-attachments/assets/a4f1fa04-6670-403f-acb0-826e6fd1d53c" />

Cross-Domain Resilience Dashboard: Cyber + Physical (NIS2 + KRITIS-DachG)
The Problem: The KRITIS-DachG (in force since March 17, 2026) is the first German law mandating physical and organizational resilience alongside cybersecurity. Operators must now report incidents to both the BSI (cyber) and the BBK (physical) within 24 hours, maintain 24/7 contact points, and conduct risk analyses covering natural disasters, sabotage, and terrorism—not just cyber threats. Most SOCs have no tooling to correlate cyber and physical security events. ​
Project Overview: Create a unified SOC analyst frontend that:
 
Correlates cyber alerts (SIEM, IDS) with physical security events (access control logs, CCTV motion detection, perimeter breach sensors, building management systems)
 
Flags incidents that trigger both BSI (cyber) and BBK (physical) reporting obligations under the dual-reporting regime
 
Visualizes facility risk posture with cyber-physical heatmaps (e.g., "Server room access breach + failed VPN login = potential insider threat")
 
Manages the 24/7 contact point roster and escalation chains required by §8 KRITIS-DachG
 
Tracks resilience plan compliance (business continuity, emergency procedures, staff training) against the 4-year risk assessment cycle
Frontend Features: Dual-pane incident view (cyber vs. physical), unified reporting decision tree (BSI only / BBK only / both), facility floor plan overlay with security event markers, contact point availability dashboard, and resilience plan task tracker with BBK audit evidence collection.
Why It Matters: This is a brand-new market gap. The KRITIS-DachG registration deadline is July 17, 2026, and initial BBK audits are planned for 2027. Companies are scrambling to integrate physical and cyber security operations. Management is now personally liable for non-compliance (up to €10M fines), so boards urgently need visibility into cross-domain resilience.


# 🛡️ Cross-Domain Resilience Dashboard: Cyber + Physical (NIS2 + KRITIS-DachG)

> **Project Specification v1.0.0** | 2026-07-13 | Project Specification & Frontend Blueprint

A unified SOC analyst frontend that correlates cyber alerts (SIEM, IDS) with physical security events (access control, CCTV, perimeter sensors, BMS) and automates dual BSI/BBK reporting under the new KRITIS-DachG regime.

---

## 📋 Table of Contents

- [Executive Summary](#executive-summary)
- [Regulatory Context](#regulatory-context)
- [Core Modules](#core-modules)
- [UI Views](#ui-views)
- [Technical Architecture](#technical-architecture)
- [Implementation Roadmap](#implementation-roadmap)
- [Competitive Landscape](#competitive-landscape)
- [Success Metrics](#success-metrics)
- [Project Files](#project-files)
- [Getting Started](#getting-started)

---

## Executive Summary

The KRITIS-DachG (in force since March 17, 2026) creates a brand-new compliance market. Approximately 2,000 operators across 11 sectors must now integrate physical and cyber security operations for the first time under federal law. Most SOCs have zero tooling for cross-domain correlation.

### ⚠️ Critical Deadline Update (July 2026)

The originally cited **July 17, 2026** registration deadline has been removed by Bundestag amendment (June 12, 2026). The new deadline will be **3 months after the KRITIS-Ordinance (KritisV) enters force** — still pending Bundesrat approval.

| Metric | Value |
|--------|-------|
| **Maximum Fine** | €10,000,000 or 2% of global revenue |
| **Affected Operators** | ~2,000 across 11+ sectors |
| **Reporting Window** | 24 hours (initial), 1 month (detailed) |
| **First Audits** | Planned for 2027 |

---

## Regulatory Context

### KRITIS-DachG (In Force: March 17, 2026)

*Gesetz zur Stärkung der Resilienz Kritischer Anlagen* — implements EU Directive 2022/2557 (CER Directive). The first German law mandating **physical and organizational resilience** across sectors.

**Affected Sectors:** Energy, Transport, Banking, Health, Water, Digital Infrastructure, Public Administration, Space, Food, Production, Research, Social Insurance, Waste Disposal

### NIS2UmsuCG (Complementary)

*Gesetz zur Umsetzung der NIS2-Richtlinie* — governs digital cybersecurity. Both laws can apply simultaneously to the same operator.

### Key Legal Sections

| Section | Title | Key Requirements |
|---------|-------|-----------------|
| **§8** | Registration & 24/7 Contact Point | Registration via BBK/BSI joint portal; mandatory 24/7 contact point |
| **§12** | Risk Analysis (4-Year Cycle) | Comprehensive risk assessment every 4 years; first due 9 months post-registration |
| **§13** | Resilience Plan & Measures | Documented TOM (technical, organizational, personnel measures); first due 10 months post-registration |
| **§16** | Evidence & Audit | BBK can request evidence, conduct audits, demand remediation plans |
| **§18** | Incident Reporting (Dual) | 24h initial report to joint BBK/BSI point; 1-month detailed report |
| **§20** | Management/Board Duties | Personal liability with private assets; management bans up to 5 years |

---

## Core Modules

### M1: Unified Incident Correlation Engine
Correlates cyber alerts (SIEM, IDS, EDR) with physical events (access control, CCTV, perimeter sensors, BMS) using temporal proximity, spatial relationships, and asset mapping.

**Key Correlation Scenarios:**
- **Insider Threat** — Server room breach + failed VPN login → **BOTH** (BSI + BBK)
- **OT/ICS Compromise** — Control room intrusion + SCADA anomaly → **BOTH**
- **Supply Chain Attack** — Vendor physical access + malware deployment → **BOTH**
- **Drone Incident** — Unauthorized overflight + RF interference → **BOTH**
- **Natural Disaster** — Environmental alert + IT outage → **BBK** (primary) + **BSI**

### M2: Dual-Reporting Decision Tree
Interactive decision engine per §18 KRITIS-DachG. Automatically classifies incidents as **BSI-only**, **BBK-only**, or **BOTH** with 6-step wizard workflow and 24h countdown timer.

### M3: Facility Cyber-Physical Heatmap
Interactive SVG floor plans with real-time risk scoring (0-100), pulsing incident markers, layer toggles, and historical replay.

### M4: 24/7 Contact Point & Escalation Manager
Manages §8 mandatory contact point with automated check-in verification, escalation chains (Primary → Secondary → Management → Board), and availability dashboards.

### M5: Resilience Plan Compliance Tracker
4-year cycle management for §12 risk analyses, §13 resilience plans, §16 audit evidence, and §20 management oversight. Includes Kanban boards, document vaults, and audit readiness scoring.

---

## UI Views

| View | Purpose | Layout |
|------|---------|--------|
| **V1: Operations Center** | Main SOC dashboard | 12-column grid with 6 widgets |
| **V2: Incident Detail** | Dual-pane investigation | 50/50 split + bottom analysis panel |
| **V3: Reporting Center** | BSI/BBK report wizard | 6-step stepper workflow |
| **V4: Facility Manager** | Interactive floor plans | Map-centric with sidebar |
| **V5: Compliance & Audit** | 4-year cycle tracking | Timeline + detail panels |

---

## Technical Architecture

### Frontend
- **Framework:** React 18+ with TypeScript
- **State:** Redux Toolkit + RTK Query
- **UI:** Material-UI v5 / Ant Design
- **Visualization:** D3.js, Chart.js, Leaflet/OpenLayers
- **Real-Time:** WebSocket (Socket.io) / SSE
- **Maps:** SVG-based floor plans with Canvas overlay

### Backend
- **API:** REST + GraphQL
- **Auth:** OAuth 2.0 / OIDC with MFA
- **Authorization:** RBAC with domain roles (Cyber Analyst, Physical Security, Compliance Officer, SOC Manager, Board Viewer, Admin)
- **Event Bus:** Apache Kafka / RabbitMQ
- **SIEM Connectors:** Splunk, QRadar, Microsoft Sentinel, Elastic (syslog, CEF, LEEF)

### Core Data Entities
- **Incident** — Unified cyber-physical with correlation metadata
- **SecurityEvent** — Raw normalized events from all sources
- **Facility** — Site → Building → Floor → Zone → Room hierarchy
- **Asset** — IT assets with physical location mapping
- **ContactPoint** — 24/7 roster with availability tracking
- **ResiliencePlan** — Documents, tasks, evidence linkage

---

## Implementation Roadmap

| Phase | Duration | Target |
|-------|----------|--------|
| **Phase 1: MVP** | 8-10 weeks | Proof of concept for early adopters preparing for registration |
| **Phase 2: Core** | 12-16 weeks | Production-ready for Q4 2026 risk analysis/resilience plan deadlines |
| **Phase 3: Enterprise** | 16-20 weeks | Full scale for 2027 BBK audit readiness |

---

## Competitive Landscape

| Category | Examples | Limitation |
|----------|----------|------------|
| **Traditional SIEMs** | Splunk, QRadar, Sentinel | Cyber-only; no physical correlation; no KRITIS compliance |
| **Physical Security** | Genetec, Lenel, Honeywell | Physical-only; no cyber context; no regulatory reporting |
| **GRC Platforms** | ServiceNow GRC, RSA Archer | Compliance-focused; no real-time operations; no facility visualization |

**Our Unique Value:** First platform correlating cyber-physical events with built-in KRITIS-DachG §8-§20 compliance automation.

---

## Success Metrics

### Operational KPIs
- Mean Time to Detect correlated incidents (MTTD-C)
- Reporting accuracy rate (correct BSI/BBK classification)
- 24/7 contact point availability percentage
- Incident-to-report submission time (within 24h SLA)

### Compliance KPIs
- Risk assessment completion (4-year cycle adherence)
- Resilience plan task completion percentage
- BBK audit deficiency findings (target: zero critical)
- Management liability exposure score reduction

### Business KPIs
- Hours saved per incident report vs manual process
- Compliance preparation effort reduction (FTE weeks)
- Board confidence in resilience posture
- Avoided fines (risk reduction quantified in €)

---

## Project Files

| File | Description | Format |
|------|-------------|--------|
| **[Complete Specification](KRITIS_Cross_Domain_Resilience_Dashboard_Complete_Specification.json)** | Full JSON data model with all modules, views, and workflows | JSON |
| **[HTML Specification](KRITIS_Cross_Domain_Resilience_Dashboard.html)** | Styled, navigable document with internal links and dark theme | HTML |
| **[Wireframes](KRITIS_Dashboard_Wireframes.json)** | Detailed UI wireframe specifications for all 5 views | JSON |
| **[Technical Modules](KRITIS_Cross_Domain_Resilience_Dashboard_Spec.json)** | Core module specifications and correlation scenarios | JSON |

---

## Getting Started

1. **Review the [HTML Specification](KRITIS_Cross_Domain_Resilience_Dashboard.html)** for the full visual overview with internal navigation
2. **Import the [JSON Complete Spec](KRITIS_Cross_Domain_Resilience_Dashboard_Complete_Specification.json)** into your project management tool
3. **Reference the [Wireframes](KRITIS_Dashboard_Wireframes.json)** for frontend implementation details
4. **Start with Phase 1 MVP** (8-10 weeks) targeting the registration deadline

---

## License & Compliance

This specification is designed for **German Critical Infrastructure Operators** subject to:
- **KRITIS-DachG** (Gesetz zur Stärkung der Resilienz Kritischer Anlagen)
- **NIS2UmsuCG** (Gesetz zur Umsetzung der NIS2-Richtlinie)
- **EU CER Directive** (2022/2557)

**Generated:** 2026-07-13  
**Version:** 1.0.0  
**Author:** Ashley Jordan Chihiya
