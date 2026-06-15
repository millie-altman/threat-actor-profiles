# Threat Actor Profile: Lazarus Group
## DPRK State-Sponsored | Financial Theft & Espionage | Dual-Mission Operations

**Analyst:** Millie Altman
**Classification:** UNCLASSIFIED // FOR PORTFOLIO USE
**MITRE ATT&CK ID:** G0032
**Profile Version:** 1.0
**Last Updated:** June 2026
**Primary Sources:** MITRE ATT&CK v19 (Updated May 2026), FBI/CISA/Treasury Advisory AA22-108A, CISA Advisory AA24-207A, FBI Bybit Attribution Statement (March 2025), DOJ Indictment (2018, 2021), Mandiant/Google Threat Intelligence, Unit 42 North Korean Threat Assessment (2024)

---

## Quick Reference

| Attribute | Detail |
|---|---|
| **Common Name** | Lazarus Group |
| **Also Known As** | HIDDEN COBRA, Guardians of Peace, ZINC, NICKEL ACADEMY, Diamond Sleet, Labyrinth Chollima, TraderTraitor, Whois Team |
| **Origin** | Democratic People's Republic of Korea (DPRK) — state-sponsored |
| **Active Since** | At least 2009 |
| **Sponsoring Entity** | Reconnaissance General Bureau (RGB) — DPRK primary intelligence and cyber operations directorate |
| **Primary Motivation** | Dual-mission: financial theft to fund DPRK weapons programs + strategic espionage in support of regime objectives |
| **Primary Targeting** | Financial institutions, cryptocurrency exchanges, defense contractors, government entities, technology companies, healthcare, media |
| **Defining Tradecraft** | Social engineering via fake job offers (Operation DreamJob), supply chain compromise, custom malware toolsets, cryptocurrency theft at scale, simultaneous espionage and ransomware operations |
| **Infrastructure** | Dedicated C2 infrastructure, acquired domains with SSL certificates, compromised third-party sites, Tornado Cash and mixing services for cryptocurrency laundering |
| **Threat Level** | **CRITICAL** for financial sector, cryptocurrency, and defense-adjacent organizations |

---

## Strategic Assessment

Lazarus Group is assessed with high confidence as one of the most operationally versatile and financially consequential nation-state threat actors currently active. Unlike most nation-state cyber programs that prioritize either intelligence collection or disruption, Lazarus Group operates a genuine dual-mission program, conducting large-scale financial theft to generate hard currency for a sanctions-burdened regime while simultaneously executing espionage operations targeting defense, government, and technology sectors aligned with DPRK strategic priorities.

The financial dimension distinguishes Lazarus Group from every other nation-state actor in the threat landscape. The group is assessed to have stolen over $3 billion in cryptocurrency between 2017 and 2023 according to the United Nations. The February 2025 theft of approximately $1.5 billion from the Bybit cryptocurrency exchange, attributed by the FBI in March 2025, represents the single largest cryptocurrency heist in history. These funds are assessed to directly support DPRK's ballistic missile and nuclear weapons programs, which are subject to international sanctions restricting conventional revenue streams. Lazarus Group's cyber operations are therefore not merely an intelligence or disruption tool — they are a primary national revenue mechanism.

The espionage dimension is equally significant. Lazarus Group's subunits, particularly Andariel, conduct targeted intrusions against defense contractors, government agencies, and research institutions to collect intelligence on military technology, nuclear programs, and foreign policy that supports DPRK strategic planning. CISA confirmed in August 2024 that Andariel actors fund their espionage operations in part through ransomware attacks against U.S. healthcare entities, in some instances conducting ransomware operations and espionage against the same target on the same day.

What makes the Lazarus Group particularly difficult to counter is this operational flexibility. The group adapts continuously — shifting targets, developing new malware families, and exploiting emerging platforms (Web3, AI developer tools, cryptocurrency infrastructure) as they gain prominence. Attribution is further complicated by the RGB's practice of reorganizing units and sharing personnel, infrastructure, and tooling across subgroups, making clean attribution of specific operations challenging even for sophisticated defenders.

---

## Targeting Profile

### Confirmed Targeted Sectors
- Cryptocurrency exchanges and virtual asset service providers (VASPs)
- Financial institutions — banks, SWIFT infrastructure, payment processors
- Defense contractors and the defense industrial base
- Government agencies — foreign ministries, military, intelligence-adjacent
- Technology companies — particularly software supply chains and developer toolchains
- Healthcare and pharmaceutical
- Energy sector
- Media and entertainment
- Nuclear research and aerospace organizations

### Geographic Focus
- Global — one of the most geographically broad threat actors documented
- United States (primary — financial and defense targets)
- South Korea (primary — persistent espionage priority)
- Japan, Europe, Southeast Asia
- Cryptocurrency infrastructure globally, regardless of jurisdiction

### Target Selection Logic

Lazarus Group selects targets along two parallel axes, financial value and intelligence value. For financial operations, targets are selected based on the volume of accessible cryptocurrency or financial assets and the likelihood of successful theft before detection. Cryptocurrency exchanges, DeFi protocols, and Web3 infrastructure are prioritized because of their high asset density, relatively immature security postures compared to traditional banking, and the pseudonymous nature of blockchain transactions that enables laundering. For espionage operations, targets are selected based on their access to information relevant to DPRK's military modernization priorities — defense contractors with weapons system data, government entities with foreign policy positions, and research institutions working on nuclear or aerospace technology.

---

## Operational Tradecraft

Lazarus Group's defining operational characteristic is the combination of sophisticated social engineering with custom malware toolsets developed specifically for each campaign. The group invests heavily in establishing trust before delivering payloads — fake job recruiters on LinkedIn, fraudulent skill assessment tests, trojanized developer tools — creating a victim interaction model where the target initiates the compromise rather than receiving an unsolicited phishing email.

The group maintains a large and continuously evolving malware ecosystem, including BLINDINGCAN, COPPERHEDGE, DTRACK, MATA, AppleJeus, CookiePlus, and dozens of other families, giving them flexibility to target Windows, macOS, and Linux environments across multiple sectors. Unlike LOTL-focused actors like Volt Typhoon, Lazarus Group frequently deploys custom tooling, reflecting the RGB's substantial investment in malware development capability. Dwell time varies by mission — financial operations tend to be faster and more disruptive, while espionage operations follow longer, more patient collection patterns.

---

## Full Kill Chain Analysis

### Stage 1: Initial Access

| Technique | ATT&CK ID | Detail |
|---|---|---|
| Phishing: Spearphishing via Service | T1566.003 | Contacts targets on LinkedIn, Telegram, and other platforms posing as recruiters offering high-salary job opportunities (Operation DreamJob) |
| Phishing: Spearphishing Attachment | T1566.001 | Delivers weaponized documents, trojanized software installers, and archive files disguised as skill assessment tests or job application materials |
| Supply Chain Compromise | T1195.002 | Modified CyberLink software installer distributed via legitimate update mechanism (November 2023); compromised software used by thousands of organizations |
| Trusted Relationship | T1199 | Leverages compromised vendor and partner email chains to deliver payloads to downstream targets |
| Exploit Public-Facing Application | T1190 | Exploits vulnerabilities in internet-facing systems when social engineering is not applicable |
| Watering Hole | T1189 | Deploys malicious/typosquat websites targeting specific developer and cryptocurrency communities |

**CTI Analyst Note:** Operation DreamJob is Lazarus Group's most consistently successful initial access methodology and has been active since at least 2019. The campaign targets employees at high-value organizations — defense contractors, aerospace companies, nuclear facilities, cryptocurrency firms — with tailored job offers. In December 2024, Kaspersky reported the campaign expanded to target nuclear sector employees using compromised archive files disguised as IT professional skill assessments to deliver the CookiePlus backdoor. The social engineering investment is analytically significant — it suggests Lazarus Group has assessed that employee trust manipulation is more reliable than technical exploitation for gaining initial access to hardened targets.

---

### Stage 2: Execution

| Technique | ATT&CK ID | Detail |
|---|---|---|
| Command and Scripting Interpreter: PowerShell | T1059.001 | PowerShell used for payload execution and post-compromise activity |
| Command and Scripting Interpreter: Unix Shell | T1059.004 | Shell execution in Linux and macOS environments |
| User Execution: Malicious File | T1204.002 | Victims execute trojanized installers, macro-enabled documents, or archive files delivered via social engineering |
| Native API | T1106 | Direct Windows API calls used by custom malware to evade detection |
| Scheduled Task / Job | T1053.005 | Scheduled tasks used to execute malware components and maintain persistence |

---

### Stage 3: Persistence

| Technique | ATT&CK ID | Detail |
|---|---|---|
| Boot or Logon Autostart: Registry Run Keys | T1547.001 | Malware components registered in Run keys for persistence across reboots |
| Create or Modify System Process: Windows Service | T1543.003 | Backdoors installed as Windows services to survive reboots |
| Server Software Component: Web Shell | T1505.003 | Web shells deployed on compromised internet-facing servers for persistent re-entry |
| Scheduled Task / Job | T1053.005 | Scheduled tasks maintain execution of backdoor components |

**CTI Analyst Note:** Lazarus Group backdoors, particularly BLINDINGCAN and COPPERHEDGE, are designed for long-term persistence and stealth. The group's financial operations typically involve shorter dwell times focused on rapid asset theft, while espionage operations (particularly by Andariel subunit) maintain persistent access for extended intelligence collection.

---

### Stage 4: Privilege Escalation & Credential Access

| Technique | ATT&CK ID | Detail |
|---|---|---|
| OS Credential Dumping | T1003 | Credential extraction from compromised systems for lateral movement |
| Credentials from Password Stores | T1555 | Extracts credentials stored in browsers and credential managers |
| Exploitation for Privilege Escalation | T1068 | Exploits local vulnerabilities to elevate privileges post-compromise |
| Valid Accounts | T1078 | Uses harvested credentials to authenticate to additional systems and services |
| Steal Application Access Token | T1528 | Harvests cryptocurrency wallet private keys and API tokens for financial theft |

---

### Stage 5: Defense Evasion & Discovery

| Technique | ATT&CK ID | Detail |
|---|---|---|
| Obfuscated Files or Information | T1027 | Malware components heavily obfuscated; DLL side-loading used to blend with legitimate processes |
| DLL Side-Loading | T1574.002 | Legitimate applications used to load malicious DLLs — observed in 2022 operations |
| Masquerading | T1036 | Malware named to resemble legitimate system files and applications |
| Indicator Removal | T1070 | Cleans forensic artifacts to hinder investigation |
| File and Directory Discovery | T1083 | Enumerates file systems for sensitive data, including cryptocurrency wallets and keys |
| System Information Discovery | T1082 | Profiles victim systems before deploying stage-specific payloads |
| Security Software Discovery | T1518.001 | Identifies installed security tools to inform evasion strategy |
| Network Service Discovery | T1046 | Maps internal network for lateral movement targeting |

**CTI Analyst Note:** Lazarus Group's use of DLL side-loading — loading malicious DLLs via legitimate, signed executables — is a deliberate evasion technique that exploits the trust extended to signed applications by endpoint security tools. This technique appeared in the November 2023 CyberLink supply chain compromise and has been documented across multiple 2022-2024 campaigns.

---

### Stage 6: Lateral Movement

| Technique | ATT&CK ID | Detail |
|---|---|---|
| Remote Services: SMB/Windows Admin Shares | T1021.002 | Lateral movement within compromised networks using harvested credentials |
| Lateral Tool Transfer | T1570 | Transfers malware components and tools across compromised hosts |
| Remote Services: SSH | T1021.004 | SSH used for lateral movement in Linux and macOS environments |
| Software Deployment Tools | T1072 | Abuses software management infrastructure for lateral movement in enterprise environments |

---

### Stage 7: Collection & Exfiltration

| Technique | ATT&CK ID | Detail |
|---|---|---|
| Data from Local System | T1005 | Collects sensitive files, documents, and credentials from compromised hosts |
| Data from Network Shared Drive | T1039 | Accesses network shares for bulk data collection |
| Archive Collected Data | T1560 | Compresses data prior to exfiltration |
| Exfiltration Over C2 Channel | T1041 | Primary exfiltration method — data transmitted over established C2 |
| Financial Theft | T1657 | Cryptocurrency theft via compromised wallet private keys, exchange API tokens, and fraudulent blockchain transactions — primary revenue mechanism for DPRK weapons programs |

**CTI Analyst Note:** For financial operations, the "exfiltration" step is cryptocurrency transfer, not file theft. Lazarus Group has developed sophisticated cryptocurrency laundering tradecraft, including the use of mixing services, chain-hopping between blockchains, and the now-sanctioned Tornado Cash protocol to obscure the origin of stolen funds. The $1.5 billion stolen from Bybit in February 2025 was rapidly distributed across thousands of wallets and multiple blockchains in an attempt to make tracing difficult. The FBI and blockchain analytics firms tracked the funds in real time — demonstrating that on-chain forensics is an increasingly powerful counter to cryptocurrency theft.

---

### Stage 8: Impact

| Technique | ATT&CK ID | Detail |
|---|---|---|
| Data Encrypted for Impact | T1486 | Ransomware deployed by Andariel subunit against U.S. healthcare targets — funds espionage operations |
| Disk Wipe | T1561 | Destructive wiper malware deployed in high-profile operations (Sony Pictures 2014, DarkSeoul 2013) |
| Service Stop | T1489 | Terminates services prior to wiper or ransomware deployment |
| Defacement | T1491 | Website defacement used in politically motivated operations |

---

## Complete ATT&CK TTP Matrix

| Tactic | Technique | ID |
|---|---|---|
| Reconnaissance | Gather Victim Identity Information | T1589 |
| Reconnaissance | Search Social Media | T1593.001 |
| Resource Development | Acquire Infrastructure: Domains | T1583.001 |
| Resource Development | Obtain Capabilities: Malware | T1588.001 |
| Resource Development | Compromise Infrastructure | T1584 |
| Initial Access | Phishing: Spearphishing via Service | T1566.003 |
| Initial Access | Phishing: Spearphishing Attachment | T1566.001 |
| Initial Access | Supply Chain Compromise | T1195.002 |
| Initial Access | Trusted Relationship | T1199 |
| Initial Access | Exploit Public-Facing Application | T1190 |
| Initial Access | Watering Hole | T1189 |
| Execution | Command and Scripting: PowerShell | T1059.001 |
| Execution | Command and Scripting: Unix Shell | T1059.004 |
| Execution | User Execution: Malicious File | T1204.002 |
| Execution | Scheduled Task / Job | T1053.005 |
| Execution | Native API | T1106 |
| Persistence | Boot or Logon Autostart: Registry Run Keys | T1547.001 |
| Persistence | Create or Modify System Process: Windows Service | T1543.003 |
| Persistence | Server Software Component: Web Shell | T1505.003 |
| Privilege Escalation | Exploitation for Privilege Escalation | T1068 |
| Defense Evasion | Obfuscated Files or Information | T1027 |
| Defense Evasion | DLL Side-Loading | T1574.002 |
| Defense Evasion | Masquerading | T1036 |
| Defense Evasion | Indicator Removal | T1070 |
| Credential Access | OS Credential Dumping | T1003 |
| Credential Access | Credentials from Password Stores | T1555 |
| Credential Access | Steal Application Access Token | T1528 |
| Discovery | File and Directory Discovery | T1083 |
| Discovery | System Information Discovery | T1082 |
| Discovery | Security Software Discovery | T1518.001 |
| Discovery | Network Service Discovery | T1046 |
| Lateral Movement | Remote Services: SMB/Windows Admin Shares | T1021.002 |
| Lateral Movement | Remote Services: SSH | T1021.004 |
| Lateral Movement | Lateral Tool Transfer | T1570 |
| Collection | Data from Local System | T1005 |
| Collection | Data from Network Shared Drive | T1039 |
| Collection | Archive Collected Data | T1560 |
| Command & Control | Application Layer Protocol: Web Protocols | T1071.001 |
| Command & Control | Encrypted Channel | T1573 |
| Command & Control | Non-Standard Port | T1571 |
| Command & Control | Proxy | T1090 |
| Exfiltration | Exfiltration Over C2 Channel | T1041 |
| Impact | Data Encrypted for Impact (Ransomware) | T1486 |
| Impact | Disk Wipe | T1561 |
| Impact | Financial Theft | T1657 |

---

## Campaign History

### Bybit Cryptocurrency Heist (February 2025)
The FBI attributed the theft of approximately $1.5 billion from Bybit — one of the world's largest cryptocurrency exchanges — to Lazarus Group in March 2025. The attack compromised Bybit's cold wallet infrastructure, enabling the unauthorized transfer of Ethereum and related tokens. This is assessed as the single largest cryptocurrency heist in history. Following the theft, Lazarus Group rapidly distributed funds across thousands of wallets and multiple blockchain networks in a laundering operation tracked in real time by the FBI and blockchain analytics firms. The scale of this operation underscores Lazarus Group's cryptocurrency theft capability and the DPRK's dependence on cyber-enabled financial crime to sustain weapons programs under international sanctions.

### Operation DreamJob — Nuclear Sector Expansion (December 2024)
Kaspersky reported that Lazarus Group expanded its long-running Operation DreamJob campaign to target employees of nuclear-related organizations in December 2024. Attackers used compromised archive files masquerading as IT professional skill assessment tests to deliver CookiePlus — a new modular backdoor disguised as an open-source plugin — enabling persistent access and intelligence collection from nuclear sector targets. This expansion is analytically significant as it directly connects Lazarus Group's social engineering capability to DPRK nuclear intelligence collection requirements.

### Operation 99 — Web3 Developer Targeting (January 2025)
Lazarus Group launched Operation 99 in January 2025, targeting software developers in the Web3 and cryptocurrency sectors. The campaign used fake recruiter personas on professional networking platforms to lure developers into cloning malicious code repositories, delivering malware that harvested cryptocurrency wallet credentials and development environment access. This operation demonstrates Lazarus Group's adaptation to target upstream developers rather than end-user cryptocurrency holders — a supply chain approach to cryptocurrency theft.

### TraderTraitor / AppleJeus Cryptocurrency Campaign (2018–Present)
Lazarus Group's TraderTraitor campaign targets cryptocurrency industry employees, exchanges, and DeFi platforms using trojanized cryptocurrency trading applications and fake job offers. FBI/CISA/Treasury Advisory AA22-108A documented the campaign in detail. Documented thefts include the $620 million Ronin Bridge theft (April 2022, attributed by FBI), $100 million Harmony Horizon Bridge theft (June 2022), and numerous smaller exchange and DeFi protocol compromises. The campaign represents the most sustained and financially destructive cryptocurrency theft operation attributed to any nation-state actor.

### CyberLink Supply Chain Compromise (November 2023)
Microsoft attributed a supply chain attack distributing a modified CyberLink software installer to the Lazarus Group (tracked as Diamond Sleet by Microsoft) in November 2023. The trojanized installer was signed with a valid CyberLink certificate and distributed through legitimate update channels, affecting organizations in the U.S., Japan, Taiwan, and Canada. The attack demonstrates Lazarus Group's willingness and capability to compromise software supply chains — consistent with the tradecraft that enabled the Sony Pictures attack and subsequent operations.

### Andariel Healthcare Ransomware + Espionage (2021–2024)
CISA Advisory AA24-207A (August 2024) confirmed that Andariel, a Lazarus Group subunit, conducts simultaneous ransomware operations against U.S. healthcare entities and cyber espionage against defense and government targets. The advisory documented instances where Andariel launched ransomware attacks and espionage operations against the same organization on the same day. Ransomware proceeds fund the espionage mission — representing a self-sustaining operational model that is analytically unique among nation-state threat actors.

### Sony Pictures Attack (November 2014)
Lazarus Group's most publicly visible destructive operation. The group compromised Sony Pictures Entertainment and deployed destructive wiper malware that destroyed approximately 70% of Sony's laptops and computers, exfiltrated unreleased films and sensitive business communications, and defaced company systems with political messaging. The U.S. government formally attributed the attack to North Korea in December 2014. The Sony operation established Lazarus Group's willingness to conduct destructive operations as a geopolitical instrument — a capability that remains part of their assessed operational repertoire.

---

## Indicators of Compromise (IOCs)

> **IOC Validity Note:** Lazarus Group IOCs rotate frequently across campaigns. File hashes, domains, and IPs degrade rapidly as the group develops new malware variants and infrastructure for each operation. Always validate against current threat intelligence feeds before actioning. All domains and URLs are defanged. For current IOC feeds, consult CISA advisories AA22-108A, AA24-207A, and MITRE ATT&CK G0032.

### Malware Families (Behavioral Indicators)

| Indicator | Type | Notes |
|---|---|---|
| BLINDINGCAN | Malware family | Full-featured RAT used in multiple Lazarus operations |
| COPPERHEDGE | Malware family | RAT used against cryptocurrency exchanges |
| DTRACK | Malware family | Information stealer used in Andariel espionage operations |
| AppleJeus | Malware family | Trojanized cryptocurrency trading app targeting macOS and Windows |
| CookiePlus | Malware family | Modular backdoor deployed in December 2024 nuclear sector targeting |
| MATA | Malware framework | Cross-platform malware framework targeting Windows, Linux, macOS |

### File Indicators

| Indicator | Type | Source | Date | Notes |
|---|---|---|---|---|
| Trojanized CyberLink installer | File | Microsoft Threat Intelligence | Nov 2023 | Signed with valid CyberLink certificate; supply chain compromise |
| `.tmp` staged malware components | File pattern | CISA AA22-108A | 2022 | Malware staged in temp directories prior to execution |

### Network Indicators

| Indicator | Type | Source | Date | Notes |
|---|---|---|---|---|
| Tornado Cash protocol | Service | FBI/Treasury | 2022–2025 | Primary cryptocurrency laundering service — now sanctioned |
| SSL-certified C2 domains | Pattern | MITRE ATT&CK G0032 | Ongoing | Group acquires SSL certificates for C2 domains to evade TLS inspection |

---

## Defensive Implications

### Priority 1 — Defend Against Social Engineering via Professional Platforms
Lazarus Group's most reliable initial access vector is not a technical exploit; it is a fake job offer. Organizations with employees in high-value roles (finance, development, defense program management) should implement awareness training specifically covering recruitment-based social engineering, enforce policies against executing software received via unsolicited professional contacts, and monitor for unusual file executions following employee engagement on LinkedIn or Telegram.

### Priority 2 — Protect Cryptocurrency Infrastructure with Operational Security Controls
For organizations in the cryptocurrency sector, standard enterprise security controls are insufficient. Cold wallet access should require multi-party authorization (MPA), no single individual or compromised credential should be able to authorize large transfers. Hardware security modules (HSMs) for key management, anomaly detection on transaction patterns, and real-time blockchain monitoring for unauthorized transfers are essential controls given Lazarus Group's demonstrated capability to move funds at speed.

### Priority 3 — Software Supply Chain Integrity Verification
The CyberLink compromise and prior supply chain operations demonstrate Lazarus Group's investment in supply chain access as a scaling mechanism. Implement software composition analysis, verify installer hashes against vendor-published values before deployment, monitor for unexpected child processes spawned by legitimate applications (DLL side-loading indicator), and restrict software installation to approved, hash-verified packages.

### Priority 4 — Monitor for DLL Side-Loading Activity
Lazarus Group's use of DLL side-loading, loading malicious DLLs via signed legitimate executables, produces Sysmon EID 7 (Image Loaded) events that can be detected with appropriate rules. Implement monitoring for unsigned DLLs loaded by signed system processes, particularly in directories outside standard system paths.

### Priority 5 — Healthcare Sector: Ransomware and Espionage Are Not Separate Threats
CISA's August 2024 advisory confirmed that Andariel conducts ransomware and espionage operations simultaneously against the same healthcare targets. Healthcare organizations should treat ransomware incidents as potential espionage vectors — not just operational disruptions — and conduct full forensic investigation of compromised environments rather than simply restoring from backup and moving on.

---

## Intelligence Gaps

- **Internal RGB structure and Lazarus subunit boundaries** — public reporting uses "Lazarus Group" as an umbrella term for multiple distinct RGB-aligned units sharing tooling and infrastructure. Clean attribution of specific operations to specific subunits remains difficult and uncertain.
- **Bybit laundering outcome** — as of the profile date, the full disposition of the $1.5 billion stolen in February 2025 has not been publicly confirmed; how much was successfully laundered versus seized or frozen is not characterized.
- **Operation 99 scope** — the full targeting breadth and victim count of the January 2025 Web3 developer campaign is not publicly characterized beyond initial reporting.
- **CookiePlus capability depth** — the full modular capability set of the CookiePlus backdoor, deployed in December 2024 nuclear sector targeting is not fully documented in public reporting.
- **DPRK weapons program financing assessment** — The specific proportion of weapons program funding attributable to Lazarus Group cryptocurrency theft versus other revenue mechanisms is assessed but not publicly confirmed with precision.

---

## Analytical Confidence Assessment

| Judgment | Confidence | Rationale |
|---|---|---|
| Lazarus Group is attributed to DPRK RGB | **High** | Formally attributed by U.S. DOJ, Treasury, CISA, FBI, and UN Panel of Experts; consistent with DPRK strategic objectives and operational patterns across 15+ years |
| Financial theft is a primary operational objective funding DPRK weapons programs | **High** | UN Panel of Experts assessment; FBI attribution of $3B+ in theft; Treasury sanctions on laundering infrastructure all corroborate |
| Bybit $1.5B theft attributed to Lazarus Group | **High** | FBI formal attribution statement March 2025; blockchain analytics corroboration |
| Operation DreamJob targets nuclear sector employees | **High** | Kaspersky December 2024 reporting; consistent with DPRK nuclear intelligence collection requirements |
| Lazarus Group and Andariel conduct simultaneous espionage and ransomware against the same targets | **High** | CISA AA24-207A formal advisory documentation |
| CookiePlus represents significant new capability | **Moderate** | December 2024 reporting confirmed deployment; full capability set not publicly characterized |

---

## References

| Source | Publisher | Date | URL |
|---|---|---|---|
| Lazarus Group — MITRE ATT&CK G0032 | MITRE | Updated May 2026 | attack.mitre.org/groups/G0032/ |
| FBI Attribution — Bybit Cryptocurrency Heist | FBI | March 2025 | fbi.gov/news/press-releases |
| CISA Advisory AA24-207A — North Korea Cyber Group Global Espionage | CISA/FBI/NSA/Allies | August 2024 | cisa.gov/news-events/cybersecurity-advisories/aa24-207a |
| FBI/CISA/Treasury Advisory AA22-108A — TraderTraitor | CISA/FBI/Treasury | April 2022 | cisa.gov/news-events/cybersecurity-advisories/aa22-108a |
| Microsoft — Diamond Sleet CyberLink Supply Chain Compromise | Microsoft Threat Intelligence | November 2023 | microsoft.com/en-us/security/blog |
| Operation DreamJob — Nuclear Sector Targeting | Kaspersky | December 2024 | securelist.com |
| Operation 99 — Web3 Developer Targeting | Group-IB / Industry Reporting | January 2025 | group-ib.com |
| North Korean Threat Groups Assessment | Unit 42 / Palo Alto Networks | October 2024 | unit42.paloaltonetworks.com |
| DOJ Indictment — Park Jin Hyok (WannaCry / Sony) | U.S. Department of Justice | September 2018 | justice.gov |
| DOJ Indictment — Jon Chang Hyok, Kim Il | U.S. Department of Justice | February 2021 | justice.gov |
| Mapping DPRK Groups to Government Organizations | Mandiant / Google Cloud | March 2022 | cloud.google.com/blog/topics/threat-intelligence |

---

*This profile was produced for portfolio demonstration purposes using exclusively open-source and publicly available intelligence. All analytical judgments are the author's own. This is an UNCLASSIFIED document containing no sensitive or classified information.*
