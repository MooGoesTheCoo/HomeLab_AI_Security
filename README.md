# 🛡️ Proxmox Cybersecurity, OT & AI Homelab - Note: coded by ChatGPT Experiment - Can i have ChatGPT code all, and research all so I dont have to??



> A self-contained cybersecurity training, OT/ICS laboratory and local AI environment built on an HPE ProLiant DL380p Gen8 running Proxmox VE.

---

## 🎯 Project Overview

This homelab is being built as a realistic environment for:

- 🔵 Blue Team / SOC training
- 🔴 Red Team and adversary simulation
- 🛡️ SIEM and security monitoring
- 🕵️ IOC investigation and threat hunting
- 🏭 OT / ICS cybersecurity training
- 🤖 Local AI and AI-agent experimentation
- ✍️ **Home AI** — private/local AI workloads and book-writing projects
- 🧪 Generating realistic security telemetry for detection engineering

The overall objective is to create a controlled environment where security activity can be generated, detected, investigated and analysed.

### Core training cycle

```text
┌──────────────┐
│  RED TEAM    │
│ Attack/Test  │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ Target VMs   │
│ Windows/Linux│
└──────┬───────┘
       │
       │ Logs / Telemetry
       ▼
┌──────────────┐
│  BLUE TEAM   │
│ SIEM / SOC   │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ Detection &  │
│ Investigation│
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ IOC / Threat │
│   Analysis   │
└──────────────┘
