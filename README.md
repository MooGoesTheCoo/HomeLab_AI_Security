# 🗺️ Homelab Roadmap

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [🛠️ Configuration](../../tree/configuration) | [🗺️ Roadmap](../../tree/roadmap)

[🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery) | [📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Project Purpose

This roadmap defines the planned build sequence for the homelab.

The objective is to build a capable, segmented and documented security-focused environment running on the HP ProLiant DL380p Gen8 with Proxmox VE.

The environment will ultimately provide infrastructure for:

- Virtualisation
- Blue Team / SOC training
- Wazuh
- Home AI
- OT/ICS security
- Red Team testing
- Network security testing
- Malware-analysis-safe testing environments
- Security monitoring
- Logging
- Detection engineering
- Incident response
- Cybersecurity experimentation

The roadmap is deliberately staged.

> **Do not build everything at once.**

Each stage should be validated before moving to the next.

---

# 📊 Overall Project Status

| Area | Status |
|---|---|
| Physical server identified | 🟢 Complete |
| CPU identified | 🟢 Complete |
| RAM identified | 🟢 Complete |
| Storage controller identified | 🟢 Complete |
| Proxmox installed | 🟢 Complete |
| Proxmox network identified | 🟢 Complete |
| Current network documented | 🟢 Complete |
| Network architecture documented | 🟢 Complete |
| VLAN architecture documented | 🟢 Complete |
| Configuration baseline documented | 🟢 Complete |
| Managed switch configuration | 🟡 Planned |
| VLAN implementation | 🟡 Planned |
| Firewall/routing architecture | 🟡 Planned |
| VM architecture | 🟡 In Design |
| Wazuh deployment | 🟡 Planned |
| Home AI deployment | 🟡 Planned |
| Tesla P40 deployment | 🟡 Planned |
| OT/ICS lab | 🟡 Planned |
| Red Team lab | 🟡 Planned |
| Blue Team lab | 🟡 Planned |
| Monitoring | 🔴 Not Started |
| Backup / DR | 🔴 Not Started |
| Testing / validation | 🔴 Not Started |
| Final documentation | 🔴 Not Started |

---

# 🟢 PHASE 1 — Physical Hardware Discovery

## Status: COMPLETE

The physical server has been inspected and the major hardware configuration has been established.

### Confirmed

```text
HP ProLiant DL380p Gen8

2 × Intel Xeon E5-2650 v2
16 physical cores
32 logical CPUs

256 GB installed RAM

HP Smart Array P420i
RAID-5
~1.6 TB logical storage

10 network interfaces detected

nic7 currently active

NVIDIA Tesla P40
24 GB
Planned
