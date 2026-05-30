# Threat Actor Profile: [ACTOR NAME]
## [Origin / Sponsorship] | [Primary Motivation] | [Defining Tradecraft]

**Analyst:** Millie Altman 
**Classification:** UNCLASSIFIED // FOR PORTFOLIO USE  
**MITRE ATT&CK ID:** [G#### or N/A if unassigned]  
**Profile Version:** 1.0  
**Last Updated:** [Month Year]  
**Primary Sources:** [List key sources used — e.g., CISA advisory, MITRE ATT&CK, vendor report]  

---
<!-- 
ANALYST GUIDANCE — HEADER
The subtitle line should capture three things at a glance:
1. Who they are (nation-state origin or criminal type)
2. What they want (espionage / financial / disruption / pre-positioning)
3. How they operate (defining tradecraft signature)

Example: "PRC State-Sponsored | Critical Infrastructure Pre-Positioning | Living-Off-the-Land"
Example: "Cybercriminal RaaS | Double Extortion | Vulnerability Exploitation"
-->

## Quick Reference

| Attribute | Detail |
|---|---|
| **Common Name** | [Primary name used in reporting] |
| **Also Known As** | [All known aliases — check MITRE ATT&CK associated groups] |
| **Origin** | [Country / region — note if state-sponsored or criminal] |
| **Active Since** | [Earliest confirmed activity date] |
| **Sponsoring Entity** | [Government body / criminal organization / unknown] |
| **Primary Motivation** | [Espionage / Financial / Disruption / Pre-positioning / Hacktivism] |
| **Primary Targeting** | [Sectors and geographies most frequently targeted] |
| **Defining Tradecraft** | [1-2 sentence signature — what makes this actor distinctive] |
| **Infrastructure** | [Key tools, botnets, or infrastructure patterns] |
| **Threat Level** | [CRITICAL / HIGH / MEDIUM / LOW — with brief rationale] |

---

## Strategic Assessment

<!--
ANALYST GUIDANCE — STRATEGIC ASSESSMENT
This is the most important section for demonstrating analytical tradecraft.
Do NOT just summarize what the actor does technically.
Answer: Why does this actor matter strategically?
- What is their ultimate objective beyond the immediate attack?
- What geopolitical or economic context drives their operations?
- What makes them distinctive compared to other actors with similar capabilities?
- What is the "so what" for an organization trying to prioritize defenses?

Aim for 2-4 paragraphs. Lead with the strategic significance, not the technical details.
Those come later.
-->

[2-4 paragraphs covering strategic significance, geopolitical context, and what makes
this actor's objectives distinct from other threat actors. Answer the question:
why should a defender care about this specific actor?]

---

## Targeting Profile

### Confirmed Targeted Sectors
<!--
List sectors confirmed through incident reporting or government advisories.
Do not speculate — only include sectors with documented evidence.
-->
- [Sector 1]
- [Sector 2]
- [Sector 3]

### Geographic Focus
- [Primary geography]
- [Secondary geography]

### Target Selection Logic
<!--
ANALYST GUIDANCE — TARGET SELECTION
This is where you show strategic thinking. Don't just list targets — explain WHY
this actor selects these targets. What is the logic?
- Nation-state: intelligence value, strategic pre-positioning, economic espionage
- Ransomware: payment likelihood, data sensitivity for extortion, sector vulnerability
- Hacktivism: ideological alignment, public visibility
-->

[2-3 sentences explaining the adversary's target selection rationale — what makes
an organization attractive to this specific actor.]

---

## Operational Tradecraft

<!--
ANALYST GUIDANCE — TRADECRAFT OVERVIEW
Before the kill chain breakdown, write a brief narrative about this actor's
defining operational style. This helps contextualize the technical details below.

Questions to answer:
- Do they favor stealth or speed?
- Custom tools or living-off-the-land?
- Long dwell time or smash-and-grab?
- What defensive controls do they specifically work to circumvent?
-->

[1-2 paragraphs describing the actor's operational philosophy and defining
tradecraft characteristics. What is their "style" as an adversary?]

---

## Full Kill Chain Analysis

<!--
ANALYST GUIDANCE — KILL CHAIN
Work through each stage systematically. For each technique:
- Name the tool or technique
- Map it to ATT&CK ID
- Describe what it does in this actor's specific context (not just the generic definition)
- Add an Analyst Note where the defensive or intelligence implication is non-obvious

Not every actor uses every stage. Only include stages with documented evidence.
Remove stages that don't apply and add a note explaining why (e.g., "No documented
persistence mechanisms — actor assessed to rely on re-exploitation for re-entry").
-->

### Stage 1: Initial Access

| Technique | ATT&CK ID | Detail |
|---|---|---|
| [Technique name] | [T####] | [Specific observed behavior — not just the ATT&CK definition] |
| [Technique name] | [T####] | [Specific observed behavior] |

**CTI Analyst Note:** [What is the defensive or intelligence implication of this initial
access pattern? What does it tell us about the actor's priorities or capabilities?]

---

### Stage 2: Execution

| Technique | ATT&CK ID | Detail |
|---|---|---|
| [Technique name] | [T####] | [Specific observed behavior] |

---

### Stage 3: Persistence

| Technique | ATT&CK ID | Detail |
|---|---|---|
| [Technique name] | [T####] | [Specific observed behavior] |

**CTI Analyst Note:** [Persistence mechanism implications for dwell time and detection.]

---

### Stage 4: Privilege Escalation & Credential Access

| Technique | ATT&CK ID | Detail |
|---|---|---|
| [Technique name] | [T####] | [Specific observed behavior] |

---

### Stage 5: Defense Evasion & Discovery

| Technique | ATT&CK ID | Detail |
|---|---|---|
| [Technique name] | [T####] | [Specific observed behavior] |

**CTI Analyst Note:** [What defensive tools or controls does this actor specifically
work to circumvent? What does that tell us about their operational planning?]

---

### Stage 6: Lateral Movement

| Technique | ATT&CK ID | Detail |
|---|---|---|
| [Technique name] | [T####] | [Specific observed behavior] |

---

### Stage 7: Collection & Exfiltration

| Technique | ATT&CK ID | Detail |
|---|---|---|
| [Technique name] | [T####] | [Specific observed behavior] |

**CTI Analyst Note:** [What data does this actor prioritize? What does that tell us
about their collection requirements and ultimate objectives?]

---

### Stage 8: Impact

<!--
For ransomware / destructive actors only. Remove this section for pure espionage actors
whose goal is persistence and collection without destructive impact.
-->

| Technique | ATT&CK ID | Detail |
|---|---|---|
| [Technique name] | [T####] | [Specific observed behavior] |

---

## Complete ATT&CK TTP Matrix

<!--
ANALYST GUIDANCE — TTP MATRIX
This is the at-a-glance reference table. Include ALL techniques observed across
all stages above. Organized by tactic (column in ATT&CK), not kill chain stage.
Hiring managers and analysts will use this table to quickly assess coverage.
-->

| Tactic | Technique | ID |
|---|---|---|
| Reconnaissance | [Technique] | [T####] |
| Resource Development | [Technique] | [T####] |
| Initial Access | [Technique] | [T####] |
| Execution | [Technique] | [T####] |
| Persistence | [Technique] | [T####] |
| Privilege Escalation | [Technique] | [T####] |
| Defense Evasion | [Technique] | [T####] |
| Credential Access | [Technique] | [T####] |
| Discovery | [Technique] | [T####] |
| Lateral Movement | [Technique] | [T####] |
| Collection | [Technique] | [T####] |
| Command & Control | [Technique] | [T####] |
| Exfiltration | [Technique] | [T####] |
| Impact | [Technique] | [T####] |

---

## Campaign History

<!--
ANALYST GUIDANCE — CAMPAIGNS
List documented operations in reverse chronological order (most recent first).
For each campaign include:
- Name (official or analyst-assigned)
- Timeframe
- What happened (brief — 2-4 sentences)
- Why it matters (the intelligence significance, not just the facts)

Only include campaigns with publicly documented evidence. Note your sources.
If no named campaigns exist, document observed intrusion clusters instead.
-->

### [Campaign Name] ([Year range])
[2-4 sentences: what happened, who was targeted, what techniques were used,
and why this campaign is analytically significant.]

### [Campaign Name] ([Year range])
[2-4 sentences describing the campaign and its significance.]

---

## Indicators of Compromise (IOCs)

<!--
ANALYST GUIDANCE — IOCs
Include IOCs only if sourced from credible, dated reports (government advisories,
major vendor reporting). Always note the source and date — IOCs degrade rapidly
as actors rotate infrastructure.

If no reliable current IOCs exist in public reporting, say so explicitly rather
than omitting the section. That's an honest and useful analytical statement.
Defang all URLs and domains using bracket notation: hxxps://example[.]com
-->

> **IOC Validity Note:** IOCs degrade over time as actors rotate infrastructure.
> Validate against current threat intelligence feeds before actioning.
> All domains and URLs are defanged.

### [IOC Category — e.g., Domains / IPs / File Hashes / Tools]

| Indicator | Type | Source | Date | Notes |
|---|---|---|---|---|
| [indicator] | [Domain/IP/Hash/etc.] | [Advisory or report] | [Date] | [Context] |

---

## Defensive Implications

<!--
ANALYST GUIDANCE — DEFENSIVE RECOMMENDATIONS
Do NOT write generic security advice here. Every recommendation should be
directly tied to a specific TTP this actor uses.

Structure: "[Actor] uses [technique] — therefore [specific defensive action]."

Prioritize by impact: what single control would most disrupt this actor's
kill chain? Lead with that. A good way to think about prioritization:
- What is this actor's most reliable initial access vector? Close that first.
- At what stage does this actor's operation become hardest to recover from?
  Build detection there.
- What is distinctive about their tradecraft that standard controls miss?
  Address that specifically.
-->

### Priority 1 — [Highest Impact Control]
[2-3 sentences: specific recommendation tied directly to this actor's TTPs,
explaining why this control disrupts their operations.]

### Priority 2 — [Second Priority]
[2-3 sentences.]

### Priority 3 — [Third Priority]
[2-3 sentences.]

### Priority 4 — [Additional Controls]
[Continue as needed based on the actor's kill chain.]

---

## Intelligence Gaps

<!--
ANALYST GUIDANCE — INTELLIGENCE GAPS
This section is one of the most important signals of analytical maturity.
Every real intelligence product documents what is NOT known.

Think about:
- What aspects of this actor's operations are not publicly characterized?
- What information would change your assessment if you had it?
- Where does public reporting conflict or remain uncertain?
- What collection would most reduce uncertainty about this actor?

Write each gap as a specific, answerable question — not just "more information needed."
-->

- [Specific unanswered question about this actor's operations or capabilities]
- [Specific gap in public reporting]
- [Specific uncertainty that would change the assessment if resolved]

---

## Analytical Confidence Assessment

<!--
ANALYST GUIDANCE — CONFIDENCE LEVELS
Apply confidence levels consistently:
HIGH — Multiple independent, credible sources corroborate the assessment.
       Government advisories + vendor reporting + MITRE ATT&CK all align.
MODERATE — Assessment is plausible and partially supported. Some gaps or
            conflicting information exist.
LOW — Based on limited evidence, single source, or significant inference.
      Alternative explanations are plausible.

Be honest. Overstating confidence undermines analytical credibility.
A well-reasoned LOW confidence judgment is more valuable than an unsupported
HIGH confidence claim.
-->

| Judgment | Confidence | Rationale |
|---|---|---|
| [Key analytical judgment] | **[High/Moderate/Low]** | [1-2 sentence explanation of why this confidence level is appropriate] |
| [Key analytical judgment] | **[High/Moderate/Low]** | [Rationale] |
| [Key analytical judgment] | **[High/Moderate/Low]** | [Rationale] |

---

## References

<!--
ANALYST GUIDANCE — REFERENCES
List every source used. Include:
- Full title of the document or article
- Publishing organization
- Date published or last updated
- URL

Prioritize primary sources: government advisories (CISA, NSA, FBI, NCSC),
MITRE ATT&CK entries, and major vendor threat intelligence reports (Microsoft,
Mandiant, CrowdStrike, Recorded Future, Dragos).

Secondary sources (news articles, blog posts) are acceptable for corroboration
but should not be your only source for a key analytical judgment.
-->

| Source | Publisher | Date | URL |
|---|---|---|---|
| [Document title] | [Organization] | [Date] | [URL] |
| [Document title] | [Organization] | [Date] | [URL] |

---

*This profile was produced for portfolio demonstration purposes using exclusively
open-source and publicly available intelligence. All analytical judgments are the
author's own. This is an UNCLASSIFIED document containing no sensitive or
classified information.*
