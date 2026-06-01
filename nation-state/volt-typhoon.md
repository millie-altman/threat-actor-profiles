# Threat Actor Profile: Volt Typhoon
## PRC State-Sponsored | Critical Infrastructure Pre-Positioning | Living-Off-the-Land

![Nation-State](https://img.shields.io/badge/Type-Nation--State%20%7C%20PRC-red)
![MITRE ATT&CK](https://img.shields.io/badge/ATT%26CK-G1017-red)
![Critical Infrastructure](https://img.shields.io/badge/Targeting-Critical%20Infrastructure-orange)
![TLP:CLEAR](https://img.shields.io/badge/TLP-CLEAR-white)
![Status](https://img.shields.io/badge/Status-Final-darkgreen)

**Analyst:** Millie Altman

**Classification:** UNCLASSIFIED // FOR PORTFOLIO USE  
**MITRE ATT&CK ID:** G1017  
**Profile Version:** 1.0  
**Last Updated:** June 2025  
**Primary Sources:** CISA/NSA/FBI Joint Advisories AA23-144A & AA24-038A, MITRE ATT&CK v17, Microsoft Threat Intelligence  

---

## Quick Reference

| Attribute | Detail |
|---|---|
| **Common Name** | Volt Typhoon |
| **Also Known As** | BRONZE SILHOUETTE, Vanguard Panda, DEV-0391, UNC3236, Voltzite, Insidious Taurus, DazedToad |
| **Origin** | People's Republic of China (PRC) — state-sponsored |
| **Active Since** | At least 2021 |
| **Sponsoring Entity** | Assessed: PRC government / military nexus |
| **Primary Motivation** | Strategic pre-positioning — not immediate espionage or financial gain |
| **Primary Targeting** | U.S. critical infrastructure, territories including Guam, Five Eyes allies |
| **Defining Tradecraft** | Living-off-the-land (LOTL), hands-on-keyboard, stolen credentials, long-term stealth |
| **Infrastructure** | KV Botnet — compromised SOHO routers used to proxy C2 traffic |
| **Threat Level** | **CRITICAL** for critical infrastructure and defense-adjacent organizations |

---

## Strategic Assessment

Volt Typhoon is assessed with **high confidence** as one of the most strategically significant cyber threats currently facing the United States. Unlike most nation-state actors whose primary objective is intelligence collection, Volt Typhoon's observed behavior — specifically its pattern of deep, persistent access to operational technology (OT) adjacent networks across multiple critical infrastructure sectors simultaneously — is assessed by CISA, NSA, and FBI as deliberate **pre-positioning for potential disruptive or destructive attacks** in the event of a major geopolitical crisis or military conflict involving the United States.

This distinction is critical for analysts to understand: Volt Typhoon is not primarily stealing data. It is building the capability to turn the lights off.

**Geopolitical Context:** The targeting pattern — particularly the emphasis on Guam and U.S. Pacific territories — aligns with assessed PRC strategic interest in degrading U.S. military logistics and communications capabilities in the Indo-Pacific theater in a Taiwan contingency scenario. Compromising water, power, communications, and transportation infrastructure would complicate U.S. force projection and create civilian disruption pressure.

**Analyst Assessment:** Volt Typhoon represents a category of threat that demands a fundamentally different defensive posture than traditional espionage or ransomware actors. The objective is not data theft detectable through DLP controls — it is persistent, silent access that may not be activated for months or years. Detection requires behavioral hunting, not signature-based alerting.

---

## Targeting Profile

### Confirmed Targeted Sectors
- Communications
- Energy
- Transportation systems
- Water and wastewater systems
- Defense industrial base (DIB)
- Government facilities
- IT and managed service providers

### Geographic Focus
- Continental United States
- Guam and U.S. Pacific territories *(assessed highest priority given Taiwan contingency context)*
- Australia, United Kingdom, Canada, New Zealand (Five Eyes partners)
- Singapore (Singtel breach confirmed June 2024)

### Target Selection Logic
Volt Typhoon prioritizes organizations that operate or support **lifeline sectors** — infrastructure whose disruption would create cascading civilian and military impact. Defense contractors are of elevated interest as both a source of sensitive technical information and as a pathway to DoD-connected networks.

---

## Operational Tradecraft: Living-Off-the-Land (LOTL)

Volt Typhoon's most defining and operationally significant characteristic is its **exclusive reliance on living-off-the-land techniques** — using legitimate, built-in operating system tools and utilities rather than custom malware. This is a deliberate tradecraft choice with profound defensive implications.

**Why LOTL matters for defenders:**
Traditional security tools detect threats by identifying malicious files, known malware signatures, or suspicious executables. When an adversary uses only tools that are already present and trusted on the system — `wmic`, `ntdsutil`, `netsh`, `PowerShell`, `certutil` — signature-based detection generates no alert. The adversary's activity is indistinguishable from a legitimate administrator unless defenders are specifically hunting for behavioral anomalies.

This is not a limitation of Volt Typhoon's capabilities — it is a deliberate strategic choice to maximize dwell time and minimize detection probability. CISA has observed Volt Typhoon maintaining access to some victim networks **for years** without detection.

---

## Full Kill Chain Analysis

### Stage 1: Initial Access

Volt Typhoon gains initial access primarily through exploitation of internet-facing network infrastructure — particularly edge devices, VPNs, and routers — rather than through phishing or social engineering.

| Technique | ATT&CK ID | Detail |
|---|---|---|
| Exploit Public-Facing Application | T1190 | Exploitation of vulnerabilities in Fortinet, Ivanti, Citrix, and Versa Director edge devices |
| Valid Accounts | T1078 | Use of stolen or harvested credentials to authenticate directly |
| External Remote Services | T1133 | Abuse of VPN and remote management services for initial entry |

**KV Botnet Infrastructure:** To obscure its origin and evade geo-based blocking, Volt Typhoon routes intrusion traffic through the **KV Botnet** — a network of compromised small office/home office (SOHO) routers, predominantly end-of-life Cisco and Netgear devices no longer receiving security patches. Traffic appearing to originate from a local U.S. IP address is significantly less likely to trigger geographic anomaly alerts. The botnet was disrupted by U.S. law enforcement in January 2024, but Volt Typhoon is assessed to have rebuilt or adapted its proxy infrastructure.

**SYLVANITE Initial Access Cluster:** Recent Dragos reporting (2026) identifies a separate cluster, SYLVANITE, that conducts initial exploitation of internet-facing edge devices and transfers access to Volt Typhoon (tracked as VOLTZITE by Dragos) for follow-on operations — indicating a division of labor between access acquisition and long-term persistence operations.

---

### Stage 2: Persistence & Credential Access

Once inside, Volt Typhoon prioritizes establishing persistent access and harvesting credentials for long-term, low-noise operations.

| Technique | ATT&CK ID | Detail |
|---|---|---|
| Web Shell | T1505.003 | Deploys web shells on internet-facing servers for persistent re-entry |
| Valid Accounts (Domain) | T1078.002 | Harvests and uses domain credentials to blend with legitimate user activity |
| OS Credential Dumping: NTDS | T1003.003 | Uses `ntdsutil` to dump Active Directory credentials |
| Credentials from Password Stores | T1555 | Extracts stored credentials from browsers and credential managers |

**CTI Analyst Note:** Web shells are a particularly effective persistence mechanism in environments where internet-facing servers are not regularly audited for unauthorized files. A web shell may remain dormant for months before being used — making it difficult to correlate with the original intrusion if log retention is insufficient.

---

### Stage 3: Discovery & Reconnaissance

Volt Typhoon conducts extensive internal reconnaissance using exclusively built-in Windows commands — no external tools downloaded, no signatures to detect.

**Observed LOTL Commands (from CISA incident response):**

| Command / Tool | ATT&CK ID | Purpose |
|---|---|---|
| `wmic` | T1047 | System information and process enumeration |
| `netsh` | T1016 | Network configuration and firewall rule discovery |
| `ipconfig` / `net` commands | T1016, T1087 | Network mapping, user and group enumeration |
| `PowerShell` (manual entry) | T1059.001 | Scripted reconnaissance and data collection |
| `ntdsutil` | T1003.003 | Active Directory database access |
| `vssadmin` | T1003.003 | Volume Shadow Copy access for credential extraction |

**CTI Analyst Note:** The exclusive use of built-in tools means Volt Typhoon leaves almost no artifact-based forensic evidence. Detection at this stage requires **command-line logging** (Windows Event ID 4688 with process command-line auditing enabled) and behavioral analytics that flag unusual sequences of built-in tool usage — particularly when initiated from service accounts or at unusual hours.

---

### Stage 4: Lateral Movement & OT Access

| Technique | ATT&CK ID | Detail |
|---|---|---|
| Remote Services: RDP | T1021.001 | Lateral movement using stolen credentials over RDP |
| Remote Services: SMB/Windows Admin Shares | T1021.002 | File transfer and execution via administrative shares |
| Pass the Hash | T1550.002 | Uses harvested NTLM hashes for authentication without plaintext password |
| Lateral Tool Transfer | T1570 | Moves files laterally using living-off-the-land file transfer utilities |

**OT Pre-Positioning:** The ultimate assessed objective of Volt Typhoon's lateral movement is reaching networks that interface with **operational technology (OT)** — industrial control systems, SCADA environments, and physical infrastructure management systems. CISA has confirmed Volt Typhoon has successfully moved from IT networks into OT-adjacent environments in multiple victim organizations.

---

### Stage 5: Command & Control

Volt Typhoon's C2 tradecraft is specifically designed to evade network-based detection.

| Technique | ATT&CK ID | Detail |
|---|---|---|
| Proxy: External Proxy | T1090.002 | Routes all C2 traffic through KV Botnet compromised routers |
| Encrypted Channel | T1573 | Uses encrypted communications to blend with legitimate HTTPS traffic |
| Non-Standard Port | T1571 | Uses non-standard ports to avoid protocol-based detection rules |
| Protocol Tunneling | T1572 | Tunnels traffic inside legitimate protocols |

**CTI Analyst Note:** The KV Botnet proxy layer is what makes Volt Typhoon's C2 so difficult to detect. Network defenders seeing traffic to a Cisco router IP registered to a small business in the same city have no obvious reason to flag it. Detection requires threat intelligence integration — specifically, blocklists of known KV Botnet infrastructure — and behavioral analysis of traffic patterns rather than source reputation alone.

---

### Stage 6: Defense Evasion & Anti-Forensics

| Technique | ATT&CK ID | Detail |
|---|---|---|
| Indicator Removal: File Deletion | T1070.004 | Deletes tools and artifacts after use |
| Indicator Removal: Clear Windows Logs | T1070.001 | Clears event logs to hinder forensic investigation |
| Masquerading | T1036 | Names malicious processes and files to resemble legitimate system components |
| Timestomping | T1070.006 | Modifies file timestamps to evade forensic timeline analysis |

---

## Complete ATT&CK TTP Matrix

| Tactic | Technique | ID |
|---|---|---|
| Reconnaissance | Gather Victim Host Information | T1592 |
| Resource Development | Acquire Infrastructure: VPS | T1583.003 |
| Resource Development | Compromise Infrastructure: Network Devices | T1584.008 |
| Initial Access | Exploit Public-Facing Application | T1190 |
| Initial Access | Valid Accounts | T1078 |
| Initial Access | External Remote Services | T1133 |
| Execution | Command and Scripting Interpreter: PowerShell | T1059.001 |
| Execution | Command and Scripting Interpreter: Unix Shell | T1059.004 |
| Execution | Windows Management Instrumentation | T1047 |
| Persistence | Server Software Component: Web Shell | T1505.003 |
| Persistence | Event Triggered Execution | T1546 |
| Privilege Escalation | Valid Accounts: Domain Accounts | T1078.002 |
| Defense Evasion | Masquerading | T1036 |
| Defense Evasion | Indicator Removal: File Deletion | T1070.004 |
| Defense Evasion | Indicator Removal: Clear Windows Logs | T1070.001 |
| Defense Evasion | Timestomping | T1070.006 |
| Credential Access | OS Credential Dumping: NTDS | T1003.003 |
| Credential Access | Credentials from Password Stores | T1555 |
| Discovery | System Network Configuration Discovery | T1016 |
| Discovery | Account Discovery | T1087 |
| Discovery | File and Directory Discovery | T1083 |
| Discovery | Security Software Discovery | T1518.001 |
| Discovery | System Information Discovery | T1082 |
| Discovery | Process Discovery | T1057 |
| Lateral Movement | Remote Services: RDP | T1021.001 |
| Lateral Movement | Remote Services: SMB/Windows Admin Shares | T1021.002 |
| Lateral Movement | Use Alternate Authentication Material: Pass the Hash | T1550.002 |
| Lateral Movement | Lateral Tool Transfer | T1570 |
| Collection | Data from Local System | T1005 |
| Collection | Archive Collected Data | T1560 |
| Command & Control | Proxy: External Proxy (KV Botnet) | T1090.002 |
| Command & Control | Encrypted Channel | T1573 |
| Command & Control | Non-Standard Port | T1571 |
| Command & Control | Protocol Tunneling | T1572 |
| Exfiltration | Exfiltration Over C2 Channel | T1041 |

---

## Campaign History

### KV Botnet Campaign (October 2022 – January 2024)
Volt Typhoon constructed and operated the KV Botnet — a network of hundreds of compromised SOHO routers — as a proxy layer for intrusion operations against U.S. critical infrastructure. The botnet provided Volt Typhoon with U.S.-based IP addresses to route attack traffic through, significantly degrading network defenders' ability to detect anomalous foreign-origin connections. The botnet was disrupted by a U.S. Department of Justice-authorized operation on January 31, 2024, which deleted the KV Botnet malware from infected routers. Volt Typhoon is assessed to have adapted its infrastructure following this disruption.

### U.S. Critical Infrastructure Pre-Positioning (2021 – Present)
CISA, NSA, and FBI confirmed in February 2024 that Volt Typhoon had successfully compromised organizations across communications, energy, transportation, and water sectors in the continental U.S. and Guam. The advisory assessed this activity as deliberate pre-positioning for potential destructive attacks rather than intelligence collection. Some compromises had persisted for multiple years without detection at the time of discovery.

### Singtel Breach (June 2024)
Volt Typhoon was attributed to a breach of Singapore Telecommunications (Singtel), a major telecommunications provider with global infrastructure connections. Singtel confirmed the incident and stated it had eradicated the associated malware. This breach extended documented Volt Typhoon targeting beyond U.S. borders to Five Eyes-aligned partner infrastructure.

### Australia Critical Infrastructure Targeting (2025)
Australian Security Intelligence Organisation (ASIO) director-general publicly identified Volt Typhoon in November 2025 as one of the PRC-linked groups that had attempted to access Australian critical infrastructure, including telecommunications networks — confirming the group's expansion of operations to U.S. allies.

---

## Defensive Implications for Defense Contractors

Defense contractors are of specific interest to Volt Typhoon for two reasons: proximity to DoD networks and systems, and possession of sensitive technical data relevant to PRC military planning. The following controls are most relevant given Volt Typhoon's documented tradecraft.

**1. Assume LOTL — Hunt Behavior, Not Signatures**
Traditional AV and signature-based detection will not detect Volt Typhoon. Defenders must implement behavioral detection rules specifically for unusual sequences of built-in tool usage. Enable command-line process auditing (Event ID 4688) and feed logs to a SIEM with behavioral analytics.

**2. Audit Internet-Facing Systems Regularly for Web Shells**
Web shells are a primary persistence mechanism. Implement file integrity monitoring on web-accessible directories and conduct regular audits for unexpected files on internet-facing servers.

**3. Patch Edge Devices Immediately — Especially End-of-Life Hardware**
Volt Typhoon specifically targets devices beyond manufacturer support lifecycles. Maintain an inventory of all internet-facing devices, enforce a patch SLA, and replace end-of-life hardware that cannot receive security updates.

**4. Implement Phishing-Resistant MFA on All Remote Access**
Volt Typhoon abuses valid credentials extensively. MFA enforcement — particularly FIDO2/hardware keys for privileged accounts — significantly increases the cost of this vector.

**5. Monitor for KV Botnet and Related Infrastructure**
Integrate threat intelligence feeds that include known Volt Typhoon proxy infrastructure. While the KV Botnet was partially disrupted, the group has continued adapting. CISA and partner advisories regularly publish updated IOCs.

**6. Establish IT/OT Network Visibility**
If your organization operates OT-adjacent systems, ensure monitoring visibility extends to the IT/OT boundary. Volt Typhoon's ultimate objective is reaching OT environments — a defender who can only see IT network traffic will miss the most critical phase of the intrusion.

**7. Extend Log Retention**
Volt Typhoon's dwell time can be measured in years. Standard 90-day log retention is insufficient for retrospective forensic analysis of long-term intrusions. Extend retention to at least 12 months for critical systems.

---

## Intelligence Gaps

- **Full scope of current U.S. victim network access** — Volt Typhoon's active compromises as of 2025 are not fully characterized in public reporting
- **Post-KV Botnet proxy infrastructure** — specific replacement C2 infrastructure used after the January 2024 botnet disruption is not fully documented in public sources
- **OT targeting specificity** — which specific OT systems or operational capabilities Volt Typhoon is pre-positioning to affect is not publicly assessed
- **SYLVANITE / Volt Typhoon handoff process** — the specific mechanism by which SYLVANITE transfers initial access to Volt Typhoon is not fully characterized

---

## Analytical Confidence Assessment

| Judgment | Confidence | Rationale |
|---|---|---|
| Volt Typhoon is PRC state-sponsored | **High** | Assessed by CISA, NSA, FBI, Five Eyes partners; corroborated by Microsoft Threat Intelligence |
| Primary objective is pre-positioning for disruption, not espionage | **High** | Consistent with CISA/NSA assessment; targeting pattern aligns with disruptive rather than collection objectives |
| Guam targeting reflects Taiwan contingency pre-positioning | **Moderate** | Logical inference from targeting geography and PRC strategic interests; not confirmed in public reporting |
| KV Botnet disruption degraded but did not eliminate capability | **Moderate** | Assessed based on group's resources and adaptability; no confirmed public reporting of complete cessation |
| Volt Typhoon has active access to U.S. critical infrastructure networks | **High** | Confirmed by multiple U.S. government advisories through 2025 |

---

## References

| Source | URL |
|---|---|
| CISA/NSA/FBI Advisory AA24-038A (Feb 2024) | cisa.gov/news-events/cybersecurity-advisories/aa24-038a |
| CISA/NSA Advisory AA23-144A (May 2023) | cisa.gov/news-events/cybersecurity-advisories/aa23-144a |
| MITRE ATT&CK: Volt Typhoon (G1017) | attack.mitre.org/groups/G1017/ |
| Microsoft Threat Intelligence (May 2023) | microsoft.com/en-us/security/blog/2023/05/24/volt-typhoon |
| DOJ KV Botnet Disruption (Jan 2024) | justice.gov/opa/pr/us-government-disrupts-botnet |
| Dragos 2026 OT/ICS Year in Review | dragos.com |
| CISA China Cyber Threat Overview | cisa.gov/topics/cyber-threats-and-advisories/advanced-persistent-threats/china |

---

*This profile was produced for portfolio demonstration purposes using exclusively open-source and publicly available intelligence. All analytical judgments are the author's own. This is an UNCLASSIFIED document.*
