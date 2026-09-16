# 🚀 Deployment

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [🛠️ Configuration](../../tree/configuration) | [🗺️ Roadmap](../../tree/roadmap)

[🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery) | [📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Deployment Purpose

This page documents the **physical implementation and deployment sequence** for the homelab.

The architecture and configuration pages define **what the environment should look like**.

This page defines:

> **How we will safely build it.**

The deployment process is deliberately staged so that each major change can be tested before the next dependency is introduced.

---

# 🚦 Current Deployment Status

| Area | Status |
|---|---|
| Physical server | 🟢 Operational |
| Proxmox | 🟢 Operational |
| Proxmox baseline | 🟢 Documented |
| Current network | 🟢 Operational |
| Network architecture | 🟢 Designed |
| VLAN architecture | 🟢 Designed |
| Configuration baseline | 🟢 Documented |
| Managed switch | 🟡 To be finalised |
| VLAN implementation | 🟡 Planned |
| Trunking | 🟡 Planned |
| Firewall/routing | 🟡 Planned |
| VM architecture | 🟡 In Design |
| Wazuh | 🟡 Planned |
| Tesla P40 | 🟡 Planned |
| Home AI | 🟡 Planned |
| OT/ICS | 🟡 Planned |
| Red Team | 🟡 Planned |
| Blue Team | 🟡 Planned |
| Monitoring | 🔴 Not Started |
| Backup/DR | 🔴 Not Started |
| Final testing | 🔴 Not Started |

---

# 🧭 Deployment Strategy

The homelab will be deployed in the following order:

```text
PHYSICAL HARDWARE
       │
       ▼
PROXMOX BASELINE
       │
       ▼
CURRENT NETWORK
       │
       ▼
MANAGED SWITCH
       │
       ▼
VLANs
       │
       ▼
TRUNKING
       │
       ▼
FIREWALL / ROUTING
       │
       ▼
PROXMOX VLAN NETWORKING
       │
       ▼
VM PLATFORM
       │
       ├──────────────┐
       ▼              ▼
    WAZUH          HOME AI
       │              │
       │              ▼
       │           GPU P40
       │
       ▼
BLUE TEAM
       │
       ▼
OT / ICS
       │
       ▼
RED TEAM
       │
       ▼
MONITORING
       │
       ▼
BACKUP / DR
       │
       ▼
TESTING
       │
       ▼
FINAL VALIDATION
