# 🏭 OT / ICS LAB

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [🛠️ Configuration](../../tree/configuration) | [🗺️ Roadmap](../../tree/roadmap)

[🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery) | [📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Purpose

The OT/ICS section defines the industrial control system environment within the homelab.

The purpose is to create a realistic but completely isolated environment in which OT/ICS technologies, protocols, monitoring and security controls can be studied and tested safely.

The OT environment will be treated differently from the normal IT environment.

The design principle is:

> **IT and OT must be separated, controlled and observable.**

---

# 🚦 Current OT/ICS Status

| Area | Status |
|---|---|
| OT/ICS architecture | 🟡 Planned |
| OT VLAN | 🟡 Planned |
| OT DMZ | 🟡 Planned |
| OT firewall rules | 🟡 Planned |
| PLC | 🔴 Not deployed |
| HMI | 🔴 Not deployed |
| Engineering Workstation | 🔴 Not deployed |
| Historian | 🔴 Not deployed |
| OT monitoring | 🔴 Not deployed |
| OT network sensor | 🔴 Not deployed |
| Wazuh integration | 🟡 Planned |
| IT/OT boundary monitoring | 🟡 Planned |
| OT attack simulation | 🟡 Planned |
| ICS detection engineering | 🟡 Planned |
| MITRE ATT&CK for ICS testing | 🟡 Planned |

---

# 🏗️ OT/ICS Architecture

The planned environment separates normal IT systems from the industrial environment.

```text
                         HOME NETWORK
                              │
                              ▼
                       ┌─────────────┐
                       │   FIREWALL  │
                       └──────┬──────┘
                              │
                 ┌────────────┴────────────┐
                 │                         │
                 ▼                         ▼
             IT NETWORK                OT DMZ
                 │                         │
                 │                    Controlled
                 │                    communication
                 │                         │
                 │                         ▼
                 │                    OT NETWORK
                 │                         │
                 │              ┌──────────┼──────────┐
                 │              │          │          │
                 │              ▼          ▼          ▼
                 │             HMI        PLC      Historian
                 │
                 ▼
             IT Systems
