# Lazarus Group – Threat Intelligence Report

**Date:** April 25, 2026  
**Author:** Dalton Hunter  
**Type:** APT Analysis  

---

## Executive Summary
This report provides an analytical overview of the Lazarus Group based on OSINT, dark web intelligence, and publicly available reporting. It examines actor behavior, targeting patterns, TTPs, IOCs, and overall capability and intent.

---

## Threat Actor Overview
Lazarus Group is a North Korea-linked advanced persistent threat (APT) group conducting both espionage and financially motivated cyber operations. The group has been active since at least the mid-2000s and is widely attributed to DPRK state-sponsored cyber activity.

**Also Known As:**
- HIDDEN COBRA (US Gov)
- APT38 (Mandiant)
- Labyrinth Chollima (CrowdStrike)
- ZINC / Diamond Sleet (Microsoft)

---

## Targeting & Victimology

**Primary Targets:**
- Cryptocurrency exchanges
- Banking systems (SWIFT)
- Government agencies
- Defense contractors
- Media organizations

**Pattern:**
Targets are selected based on:
- Financial value
- Intelligence value
- Weak security posture

---

## Tactics, Techniques, and Procedures (TTPs)

**Initial Access**
- Spearphishing (T1566)
- Malicious attachments

**Execution**
- PowerShell (T1059.001)
- Command shell (T1059.003)

**Persistence**
- Registry run keys (T1547)
- Scheduled tasks (T1053)

**Credential Access**
- Credential dumping (T1003)

**Defense Evasion**
- Obfuscation (T1027)
- Timestomping (T1070.006)

**Lateral Movement**
- SMB (T1021.002)
- RDP (T1021.001)

**Command & Control**
- HTTPS (T1071)
- Encrypted channels

**Exfiltration**
- C2 channels (T1041)
- Cloud services

---

## Indicators of Compromise (IOCs)

**Malicious Domains**
- tokenais[.]com
- cryptais[.]com

**C2 Infrastructure**
- hxxps://www.esilet[.]com/update/
- hxxps://sche-eg[.]org/plugins/top.php
- hxxps://dafnefonseca[.]com/wp-content/themes/top.php

**File Hashes**
- 60b3cfe2ec3100caf4afde734cfd5147f78acf58ab17d4480196831db4aa5f18
- f0e8c29e3349d030a97f4a8673387c2e21858cccd1fb9ebbf9009b27743b2e5b
- 5b40b73934c1583144f41d8463e227529fa7157e26e6012babd062e3fd7e0b03

**Malware**
- Manuscrypt (RAT)

---

## Analytic Assessment

**Threat Level: HIGH**

Lazarus Group is a highly capable state-sponsored actor with demonstrated expertise in both financial cybercrime and cyber espionage. The group’s ability to adapt tactics and maintain long-term campaigns presents a persistent global threat.

---

## Methodology
This report is based on OSINT and publicly available sources including:
- Security research reports
- Technical analysis
- News reporting

All information was verified for credibility and cross-referenced across sources.
