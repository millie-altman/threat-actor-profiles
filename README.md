# Threat Actor Profiles

**Analyst:** Millie Altman | Threat Intelligence Research  
**Focus:** Nation-State & Cybercriminal Threat Actor Analysis  
**Frameworks:** MITRE ATT&CK | Diamond Model | Cyber Kill Chain  

---

## About This Repository

This repository contains structured threat actor profiles produced as original intelligence research. Each profile follows a consistent analytical methodology and is designed to support threat-informed defensive decisions for organizations in critical infrastructure, defense, and government sectors.

Profiles are built from open-source intelligence (OSINT), including government advisories (CISA, NSA, FBI), vendor threat intelligence reporting, and the MITRE ATT&CK knowledge base. All analytical judgments include explicit confidence assessments.

**Analytical Standards Applied:**
- MITRE ATT&CK TTP mapping (current framework version cited per profile)
- Structured Key Judgments with confidence levels (High / Moderate / Low)
- Intelligence gaps documented alongside findings
- Geopolitical and strategic context included where relevant
- All profiles marked TLP:CLEAR — produced from publicly available sources only

---

## Profile Index

### Nation-State Actors

| Actor | Origin | Primary Motivation | Key Targeting | Profile |
|---|---|---|---|---|
| Volt Typhoon | China (PRC) | Strategic pre-positioning / disruption | Critical infrastructure, defense contractors, U.S. territories | [View Profile](./nation-state/volt-typhoon.md) |
| APT29 / Cozy Bear | Russia (SVR) | Strategic espionage / intelligence collection | Government, defense contractors, technology companies, NATO allies | [View Profile](./nation-state/apt29-cozy-bear.md) |

---

### Cybercriminal Actors

*Profiles coming soon.*

---

### Profiles In Progress

| Actor | Type | Status |
|---|---|---|
| APT29 / Cozy Bear | Nation-State (Russia) | Planned |
| Lazarus Group | Nation-State (DPRK) | Planned |
| Play Ransomware | Cybercriminal | See [Ransomware TIC Brief](https://github.com/millie-altman/threat-intelligence-portfolio/blob/main/finished-intelligence/ransomware-tic-brief.md) |

---

## Profile Template

Each profile in this repository follows a standardized structure to ensure consistency and analytical rigor:

```
1. Quick Reference          — key attributes at a glance
2. Strategic Assessment     — why this actor matters, geopolitical context
3. Targeting Profile        — sectors, geography, target selection logic
4. Operational Tradecraft   — defining techniques and methodologies
5. Full Kill Chain Analysis — stage-by-stage TTP breakdown with ATT&CK mapping
6. Complete ATT&CK Matrix   — all observed techniques in table format
7. Campaign History         — documented operations and incidents
8. Defensive Implications   — prioritized recommendations for defenders
9. Intelligence Gaps        — what is unknown or not publicly characterized
10. Analytical Confidence   — explicit confidence levels for all key judgments
11. References              — sourced, dated primary and secondary sources
```

The template itself is available here: [`/template/threat-actor-profile-template.md`](./template/threat-actor-profile-template.md)

---

## Repository Structure

```
threat-actor-profiles/
│
├── README.md                          ← this file
│
├── nation-state/
│   └── volt-typhoon.md                ← PRC | critical infrastructure
│
├── cybercriminal/
│   └── (coming soon)
│
└── template/
    └── threat-actor-profile-template.md
```

---

## Analytical Framework

**MITRE ATT&CK** is the primary framework used for TTP mapping across all profiles. ATT&CK version is cited in each profile to ensure accuracy over time as the framework is updated.

**Confidence Levels** follow a three-tier system used across the U.S. intelligence community:
- **High Confidence** — assessment is well-corroborated by multiple independent sources
- **Moderate Confidence** — assessment is plausible and partially corroborated; some gaps remain
- **Low Confidence** — assessment is based on limited or indirect evidence; alternative explanations exist

**TLP Designations** follow the Traffic Light Protocol standard:
- All profiles in this repository are **TLP:CLEAR** — produced from publicly available sources and suitable for unrestricted distribution

---

## Related Work

This repository is part of a broader CTI research portfolio:

| Repository | Description |
|---|---|
| [threat-intelligence-portfolio](https://github.com/millie-altman/threat-intelligence-portfolio) | Finished intelligence products, defensive architecture analysis |
| [cti-research-lab](https://github.com/millie-altman/cti-research-lab) | Threat research lab environment and analysis notes |
| [python-security-tools](https://github.com/millie-altman/python-security-tools) | CTI-focused Python tools for IOC enrichment and OSINT automation |

---

## Contact

Open to CTI analyst, threat researcher, and intelligence roles in federal civilian, DoD, and private sector environments.  
Connect on [LinkedIn](https://linkedin.com/in/millieealtman)
