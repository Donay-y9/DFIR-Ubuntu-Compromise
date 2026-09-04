# Digital Forensics Investigation Report  
## Compromised Ubuntu Server – Controlled Laboratory Environment

**Project:** DFIR-Ubuntu-Compromise  
**Type:** Portfolio / Controlled Lab Exercise  
**Date:** September 2026  
**Classification:** Internal / Portfolio Use Only  

---

## 1. Document Control

| Field                    | Details                                      |
|--------------------------|----------------------------------------------|
| Report Title             | Forensic Investigation of Compromised Ubuntu Server |
| Case / Lab ID            | LAB-DFIR-2026-001                            |
| Evidence Location        | `evidence/disk/`                             |
| Analysis Performed On    | Live system + collected artifacts            |
| Tools Used               | Native Linux commands, manual analysis       |
| Volatility Analysis      | Not performed (memory dump not acquired)     |


## 2. Executive Summary

This report documents the forensic investigation of a controlled compromise performed on an Ubuntu Server laboratory environment. The objective was to simulate a realistic attacker intrusion, collect evidence, and analyze the artifacts to identify the attack techniques used.

### Key Findings:

- A low-privileged user (`attack`) was created and granted passwordless sudo privileges.
- An additional user (`hiddenuser`) was also created and added to the sudo group.
- The attacker escalated privileges to root and executed classic reconnaissance commands (`cat /etc/passwd`, `cat /etc/shadow`).
- A simple backdoor script was planted in `/tmp/.hidden_backdoor.sh`.
- A file containing simulated stolen data was created in `/root/.secret_data.txt`.
- Command history of the root user clearly shows the attacker’s activity, including an attempt to download and execute a payload.

### Conclusion of the Investigation:

The server was successfully compromised in a controlled manner. Multiple persistence and post-exploitation artifacts were identified. Some persistence mechanisms (SSH authorized_keys and cron) were attempted but not properly captured in the final evidence package.

This laboratory exercise demonstrates skills in evidence collection, artifact analysis, and professional documentation of a Linux compromise.

## 3. Scope and Methodology

### Scope
This investigation was limited to a controlled Ubuntu Server laboratory environment. The goal was to simulate a realistic compromise and perform a post-incident analysis of the collected artifacts.

### Methodology
1. Controlled attack simulation (initial access, privilege escalation, persistence, and post-exploitation).
2. Live evidence collection from the compromised system.
3. Manual analysis of collected artifacts (logs, history files, configuration files, and suspicious scripts).
4. Identification of Indicators of Compromise (IOCs).
5. Mapping of observed techniques to the MITRE ATT&CK framework.

**Note:** A full disk image and memory dump were not acquired. Analysis was performed on collected artifacts. In a real engagement, a forensic image and memory capture would be mandatory.

---

## 4. Evidence Acquisition

Evidence was collected live from the compromised system and organized into the following structure:
evidence/
└── disk/
├── history/
├── logs/
├── other/
├── persistence/
└── users/
textThe full `syslog` file was collected but excluded from the repository due to its large size.

---

## 5. Detailed Findings

### 5.1 Initial Access & Privilege Escalation
- A user named `attack` was created with a weak password.
- Passwordless sudo privileges were granted via `/etc/sudoers.d/attack`.
- An additional user `hiddenuser` was created and added to the `sudo` group.
- Evidence: `users/group.txt`, `other/sudoers_d.txt`

### 5.2 Post-Exploitation Activity
Root command history (`history/bash_history_root.txt`) shows the following attacker actions:
- Reading `/etc/passwd` and `/etc/shadow`
- Attempting to download a payload from a malicious URL
- Making the payload executable and running it

### 5.3 Persistence Mechanisms
**Successful:**
- Backdoor script created at `/tmp/.hidden_backdoor.sh`
- Content: writes a log entry every time it is executed

**Attempted but not properly captured:**
- SSH authorized key in `/root/.ssh/`
- Cron job
- Reverse shell entry in `/root/.bashrc`

### 5.4 Data Staging / Exfiltration Simulation
- File `/root/.secret_data.txt` was created containing the text:  
  `Datos robados del servidor - Portfolio DFIR`
- SHA256 hash of the file was recorded.

---

## 6. Indicators of Compromise (IOCs)

| Type              | Indicator                                      | Notes                          |
|-------------------|------------------------------------------------|--------------------------------|
| User              | `attack`                                       | Created with sudo privileges   |
| User              | `hiddenuser`                                   | Added to sudo group            |
| File              | `/tmp/.hidden_backdoor.sh`                      | Backdoor script                |
| File              | `/root/.secret_data.txt`                       | Simulated stolen data          |
| File              | `/etc/sudoers.d/attack`                        | Passwordless sudo              |
| Command History   | `cat /etc/shadow`, `wget ... payload.sh`       | Clear attacker activity        |
| Hash (SHA256)     | See `other/hashes.txt`                         | Backdoor and secret file       |

---

## 7. MITRE ATT&CK Mapping

| Tactic                  | Technique                          | ID          | Evidence                     |
|-------------------------|------------------------------------|-------------|------------------------------|
| Initial Access          | Valid Accounts                     | T1078       | User `attack`                |
| Privilege Escalation    | Abuse Elevation Control Mechanism  | T1548.003   | sudoers.d/attack             |
| Persistence             | Create Account                     | T1136       | hiddenuser                   |
| Persistence             | Local Job Scheduling (attempted)   | T1053.003   | cron (not captured)          |
| Persistence             | SSH Authorized Keys (attempted)    | T1098.004   | authorized_keys              |
| Defense Evasion         | Hidden Files and Directories       | T1564.001   | .hidden_backdoor.sh          |
| Discovery               | Account Discovery                  | T1087       | cat /etc/passwd & shadow     |
| Command and Control     | Ingress Tool Transfer (attempted)  | T1105       | wget payload.sh              |
| Collection              | Data from Local System             | T1005       | secret_data.txt              |

---

## 8. Recommendations

1. Enforce strong password policies and disable password authentication for SSH where possible.
2. Regularly audit `/etc/sudoers` and `/etc/sudoers.d/` for unauthorized rules.
3. Monitor the creation of new users and additions to the `sudo` group.
4. Implement file integrity monitoring on critical paths (`/tmp`, `/root`, `/etc/cron*`).
5. Centralize and alert on suspicious command history patterns and authentication logs.
6. In production environments, always acquire full disk and memory images before analysis.

---

## 9. Conclusion

The controlled laboratory exercise successfully simulated a Linux server compromise. Clear evidence of privilege escalation, post-exploitation activity, backdoor installation, and data staging was identified and documented.

While some persistence mechanisms were not fully captured, the overall investigation demonstrates solid understanding of Linux DFIR processes, artifact analysis, and professional reporting.

This project serves as a practical portfolio piece showcasing hands-on skills in digital forensics an
