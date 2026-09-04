# DFIR - Compromised Ubuntu Server Investigation

## Project Overview

This repository contains a complete Digital Forensics and Incident Response (DFIR) laboratory project. A controlled compromise was performed on an Ubuntu Server, evidence was collected, and a full forensic analysis was conducted.

**Objective:** Demonstrate practical skills in Linux forensics, artifact analysis, and professional reporting.

## Laboratory Environment

- **OS:** Ubuntu Server
- **Existing stack:** Promtail + Loki + Grafana
- **Security controls present:** UFW + Fail2Ban
- **Type:** Controlled attack simulation + post-incident analysis

## Repository Structure
DFIR-Ubuntu-Compromise/
├── evidence/
│   └── disk/
│       ├── history/
│       ├── logs/
│       ├── other/
│       ├── persistence/
│       └── users/
├── report/
│   └── forensic_report.md
└── README.md
text## Key Findings

- Creation of privileged users (`attack` and `hiddenuser`)
- Passwordless sudo configuration
- Backdoor script planted in `/tmp`
- Simulated data exfiltration file
- Clear attacker commands in root bash history
- Multiple persistence techniques attempted

## Full Report

The complete forensic report is available here:  
→ [**forensic_report.md**](./report/forensic_report.md)

## MITRE ATT&CK Coverage

The investigation mapped techniques across:
- Initial Access
- Privilege Escalation
- Persistence
- Discovery
- Collection
- Command and Control


