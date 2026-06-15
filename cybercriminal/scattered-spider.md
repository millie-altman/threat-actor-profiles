# Threat Actor Profile — Scattered Spider

## Cybercriminal | Social Engineering | Identity-Based Intrusions | ALPHV Affiliate Association

![Threat Actor](https://img.shields.io/badge/Type-Cybercriminal-darkred)
![MITRE ATT\&CK](https://img.shields.io/badge/Framework-MITRE%20ATT%26CK-red)
![Sector Focus](https://img.shields.io/badge/Targeting-Enterprise%20%7C%20Hospitality%20%7C%20Telecom-blue)
![TLP](https://img.shields.io/badge/TLP-CLEAR-white)
![Status](https://img.shields.io/badge/Status-Active-darkgreen)

**Analyst:** Millie Altman
**Classification:** UNCLASSIFIED // FOR PORTFOLIO USE
**Date:** June 2026
**Aliases:** UNC3944, Octo Tempest, Muddled Libra
**Status:** Active
**Primary Sources:** CISA AA23-320A, Microsoft Threat Intelligence, CrowdStrike, Mandiant, Unit 42

---

## Executive Summary

Scattered Spider is a financially motivated cybercriminal collective known for highly effective social engineering operations, credential theft, identity abuse, and ransomware deployment. The group became widely known in 2023 after a series of high-profile intrusions targeting large enterprises, especially in hospitality, telecom, and critical services.

Unlike traditional ransomware operators that rely heavily on vulnerability exploitation, Scattered Spider specializes in human-layer intrusion. Their operations frequently involve help desk impersonation, MFA reset abuse, SIM swapping, phishing, and trusted account compromise.

Scattered Spider is strongly associated with BlackCat / ALPHV ransomware deployments, functioning as an intrusion specialist and affiliate partner rather than a ransomware developer.

**Key analytical finding:** Scattered Spider demonstrates that identity is now one of the most critical attack surfaces in enterprise security. Their tradecraft relies more on manipulating people and processes than exploiting software.

---

## Threat Overview

| Attribute              | Detail                                            |
| ---------------------- | ------------------------------------------------- |
| **Threat Type**        | Cybercriminal Collective                          |
| **Motivation**         | Financial extortion                               |
| **Primary Objectives** | Initial access, data theft, ransomware deployment |
| **First Observed**     | 2022                                              |
| **Primary Regions**    | North America, UK                                 |
| **Primary Targets**    | Hospitality, telecom, BPO, enterprise IT          |
| **Known Associations** | BlackCat / ALPHV                                  |

---

## Known Aliases

| Organization | Alias            |
| ------------ | ---------------- |
| Microsoft    | Octo Tempest     |
| Mandiant     | UNC3944          |
| CrowdStrike  | Scattered Spider |
| Unit 42      | Muddled Libra    |

---

## Operational Methodology

Scattered Spider typically follows a human-focused intrusion chain.

### Phase 1 — Reconnaissance

The group identifies:

* Employee names
* Help desk procedures
* Identity providers (Okta, Azure AD)
* MFA methods
* Organizational hierarchy

Common OSINT sources:

* LinkedIn
* Company websites
* Breach dumps
* Social media

---

### Phase 2 — Social Engineering

This is their strongest capability.

Common tactics:

* Help desk impersonation
* Password reset requests
* MFA reset manipulation
* SIM swapping
* Internal employee impersonation

**Observed pattern:** Attackers often speak fluent English and convincingly impersonate employees.

---

### Phase 3 — Credential Access

After social engineering succeeds:

* Account passwords are reset
* MFA tokens are reassigned
* SSO sessions are hijacked
* New devices are enrolled

Common identity targets:

* Okta
* Azure AD
* Duo
* VPN access

---

### Phase 4 — Privilege Escalation

Attackers may:

* Add themselves to admin groups
* Reset privileged accounts
* Create persistence accounts
* Enumerate domain trusts

---

### Phase 5 — Data Theft

Before ransomware deployment:

* Sensitive files are located
* Archives are created
* Data is exfiltrated

---

### Phase 6 — Ransomware Deployment

Frequently observed with:

* BlackCat / ALPHV
* Potential affiliate ransomware operations

---

## MITRE ATT&CK TTP Mapping

Scattered Spider is heavily identity- and social-engineering-driven.

| Tactic                   | Technique                                | ID    | Observed Behavior                   |
| ------------------------ | ---------------------------------------- | ----- | ----------------------------------- |
| **Reconnaissance**       | Gather Victim Identity Information       | T1589 | Employee profiling                  |
| **Reconnaissance**       | Gather Victim Org Information            | T1591 | Help desk procedures, org structure |
| **Initial Access**       | Phishing                                 | T1566 | Credential harvesting               |
| **Initial Access**       | Valid Accounts                           | T1078 | Credential abuse                    |
| **Credential Access**    | Multi-Factor Authentication Interception | T1111 | MFA abuse and reset manipulation    |
| **Persistence**          | Create Account                           | T1136 | New accounts created                |
| **Privilege Escalation** | Account Manipulation                     | T1098 | Admin group changes                 |
| **Discovery**            | Account Discovery                        | T1087 | User enumeration                    |
| **Discovery**            | Network Share Discovery                  | T1135 | Sensitive file discovery            |
| **Collection**           | Archive Collected Data                   | T1560 | Compression for exfiltration        |
| **Exfiltration**         | Exfiltration Over Web Service            | T1567 | Cloud uploads                       |
| **Impact**               | Data Encrypted for Impact                | T1486 | ALPHV deployment                    |

---

## Notable Campaigns

### MGM Resorts (2023)

One of the most public Scattered Spider incidents.

Observed:

* Help desk impersonation
* Credential reset abuse
* Lateral movement
* BlackCat deployment
* Major operational disruption

---

### Caesars Entertainment (2023)

Similar identity-focused intrusion:

* Social engineering
* Privileged access compromise
* Data theft
* Reported ransom payment

---

### Telecom Sector Intrusions

Repeated targeting of telecom organizations:

* SIM swapping
* Subscriber data access
* Identity compromise

---

## Indicators of Compromise (Behavioral)

Scattered Spider uses fewer static indicators than malware-centric actors.

High-confidence behavioral indicators:

### Identity Indicators

* Unusual MFA reset requests
* Help desk password resets outside normal patterns
* New device enrollment from unfamiliar geolocation
* High-volume SSO failures

### Access Indicators

* Impossible travel
* VPN logins from unusual regions
* Multiple password resets in short succession
* Account recovery abuse

### Administrative Indicators

* Unexpected privileged group changes
* Emergency admin account creation
* Unusual identity provider configuration changes

---

## Victimology

Scattered Spider often targets organizations with:

* Large help desk teams
* Outsourced support centers
* Centralized identity systems
* High customer dependence
* Large employee populations

Common sectors:

* Hospitality
* Telecommunications
* Retail
* Technology
* BPO providers

---

## Defensive Implications

**1. Harden help desk workflows**
Identity verification procedures must be resistant to social engineering.

**2. Protect MFA reset paths**
MFA enrollment changes should require elevated verification.

**3. Monitor identity providers aggressively**
Okta, Azure AD, and VPN logs are primary detection sources.

**4. Detect unusual password resets**
Help desk reset volume should be baselined.

**5. Train support staff**
Help desk personnel are now frontline defenders.

---

## Analytical Assessment

Scattered Spider is one of the clearest examples of modern cybercrime shifting from technical exploitation toward identity-first attacks.

Their success demonstrates:

* Human trust is an exploitable infrastructure
* Identity providers are critical assets
* Social engineering scales
* Traditional perimeter defenses are insufficient

**Analytical note:** Scattered Spider should be studied by CTI analysts not only as a ransomware affiliate, but as a case study in identity-centric threat evolution.

---

## Related Malware

| Malware          | Relationship                                         |
| ---------------- | ---------------------------------------------------- |
| BlackCat / ALPHV | Primary ransomware affiliate relationship            |
| LockBit          | Possible affiliate ecosystem overlap                 |
| Cl0p             | Similar extortion objectives, different access model |

---

## References

| Source                              | Publisher          | Date |
| ----------------------------------- | ------------------ | ---- |
| Scattered Spider Advisory AA23-320A | CISA               | 2023 |
| Octo Tempest Threat Profile         | Microsoft          | 2024 |
| MGM Incident Reporting              | Public Sources     | 2023 |
| Caesars Incident Reporting          | Public Sources     | 2023 |
| CrowdStrike Threat Intelligence     | CrowdStrike        | 2024 |
| Unit 42 Threat Research             | Palo Alto Networks | 2024 |

---

*This threat actor profile was produced for portfolio demonstration purposes using exclusively open-source and publicly available intelligence. This is an UNCLASSIFIED document.*
