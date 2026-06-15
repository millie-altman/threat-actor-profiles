# Cybercriminal Threat Actor Profiles

![Threat Intelligence](https://img.shields.io/badge/Focus-Cyber%20Threat%20Intelligence-darkred)
![Threat Actors](https://img.shields.io/badge/Category-Cybercriminal-blue)
![MITRE ATT\&CK](https://img.shields.io/badge/Framework-MITRE%20ATT%26CK-red)
![TLP](https://img.shields.io/badge/TLP-CLEAR-white)
![Status](https://img.shields.io/badge/Status-Active-darkgreen)

**Analyst:** Millie Altman
**Classification:** UNCLASSIFIED // PORTFOLIO USE
**Status:** Active

---

## Overview

This directory contains intelligence-driven profiles on financially motivated cybercriminal threat actors. Unlike nation-state or advanced persistent threat (APT) groups, these actors primarily operate for financial gain through ransomware, extortion, credential theft, fraud, and access brokerage.

These profiles focus on operational behavior, intrusion methodology, known campaigns, MITRE ATT&CK TTP mapping, victimology, and defensive implications.

The purpose of this collection is to document how financially motivated threat actors operate and how their tradecraft differs from espionage-driven or nation-state adversaries.

---

## Profile Index

| Threat Actor     | Category                 | Primary Motivation  | Known Associations | Profile                       |
| ---------------- | ------------------------ | ------------------- | ------------------ | ----------------------------- |
| Scattered Spider | Cybercriminal Collective | Financial Extortion | BlackCat / ALPHV   | [View](./scattered-spider.md) |

---

## Analytical Focus Areas

Each profile analyzes:

```txt id="3k81dv"
1. Executive Summary
2. Threat Overview
3. Known Aliases
4. Operational Methodology
5. MITRE ATT&CK TTP Mapping
6. Notable Campaigns
7. Behavioral Indicators
8. Victimology
9. Defensive Implications
10. Analytical Assessment
11. Related Malware
12. References
```

---

## Common Tradecraft Observed

Cybercriminal actors often rely on:

### Identity-Based Intrusion

* Social engineering
* MFA reset abuse
* Help desk impersonation
* Credential theft
* SIM swapping

### Ransomware Operations

* Double extortion
* Triple extortion
* Data leak sites
* Affiliate models

### Data Theft

* Sensitive file collection
* Cloud exfiltration
* Archive compression

### Access Monetization

* Initial access brokerage
* Credential resale
* Ransom negotiations

---

## Related Malware Analysis

These threat actor profiles connect directly to malware analysis reports in the malware-analysis repository:

| Malware          | Related Actor                    |
| ---------------- | -------------------------------- |
| BlackCat / ALPHV | Scattered Spider                 |
| LockBit          | Affiliate ecosystem overlap      |
| Cl0p             | Similar extortion objectives     |
| WannaCry         | Comparative ransomware evolution |

---

## Why This Matters

Financially motivated cybercriminal groups often move faster than nation-state actors and adapt quickly to defensive improvements.

Studying these actors helps defenders understand:

* How ransomware ecosystems operate
* How human-layer attacks bypass technical controls
* How identity has become a primary attack surface
* How modern extortion models evolve

---

## Future Additions

Planned profiles:

* TA505
* FIN7
* Wizard Spider
* Evil Corp
* LAPSUS$
* FIN12
* Karakurt
* Vice Society

---

*This directory is maintained as part of an active cyber threat intelligence portfolio focused on adversary tradecraft, ransomware ecosystems, and defensive security research.*
