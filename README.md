# DFIR - Compromised Ubuntu Server Investigation

## Project Overview

This repository contains a Digital Forensics and Incident Response (DFIR) laboratory project. A controlled compromise was performed on an Ubuntu Server, evidence was collected, and a forensic analysis was conducted.

**Objective:** Demonstrate practical skills in Linux forensics, artifact analysis, incident investigation, and professional reporting.

## Laboratory Environment

- **OS:** Ubuntu Server
- **Existing stack:** Promtail + Loki + Grafana
- **Security controls:** UFW + Fail2Ban
- **Type:** Controlled attack simulation + post-incident analysis

## Repository Structure

```text
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
```

## Key Findings

- Creation of privileged users (`attack` and `hiddenuser`)
- Passwordless sudo configuration
- Suspicious backdoor script planted in `/tmp`
- Simulated data exfiltration file
- Attacker commands identified in root bash history
- Multiple persistence techniques attempted

## Full Report

The complete forensic report is available here:

→ [Forensic Report](report/forensic_report.md)

## MITRE ATT&CK Coverage

The investigation mapped observed activity across the following tactics:

- Initial Access
- Privilege Escalation
- Persistence
- Discovery
- Collection
- Command and Control
