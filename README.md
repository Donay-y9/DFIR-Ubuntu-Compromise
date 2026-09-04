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
- Backdoor script planted in `/tmp`
- Simulated data exfiltration file
- Clear attacker commands in root bash history
- Multiple persistence techniques attempted
