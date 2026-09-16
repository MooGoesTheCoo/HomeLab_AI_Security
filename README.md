# 🧪 Testing Lab

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [🛠️ Configuration](../../tree/configuration) | [🗺️ Roadmap](../../tree/roadmap)

[🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery) | [📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Purpose

The Testing Lab provides a controlled environment for validating the homelab infrastructure, network segmentation, security monitoring and defensive capabilities.

The objective is:

> **Build → Test → Observe → Validate → Document → Improve**

Testing will be performed only against systems intentionally placed within the homelab environment.

---

# 🚦 Current Testing Status

| Area | Status |
|---|---|
| Proxmox baseline | 🟢 Verified |
| Current network connectivity | 🟢 Verified |
| Current management network | 🟢 Verified |
| VLAN testing | 🟡 Planned |
| Firewall testing | 🟡 Planned |
| Network isolation testing | 🟡 Planned |
| Wazuh detection testing | 🟡 Planned |
| Windows endpoint testing | 🟡 Planned |
| Linux endpoint testing | 🟡 Planned |
| Red Team testing | 🟡 Planned |
| Purple Team testing | 🟡 Planned |
| OT/ICS testing | 🟡 Planned |
| MITRE ATT&CK validation | 🟡 Planned |
| Backup/restore testing | 🔴 Not Started |
| Disaster recovery testing | 🔴 Not Started |

---

# 🧱 Testing Architecture

The testing environment will eventually operate across the segmented lab network.

```text
                         MANAGEMENT
                          VLAN 10
                             │
                             │
                        ┌────▼────┐
                        │ Firewall│
                        └────┬────┘
                             │
          ┌──────────────────┼──────────────────┐
          │                  │                  │
          ▼                  ▼                  ▼
      VLAN 20            VLAN 30            VLAN 40
     BLUE TEAM           HOME AI             OT/ICS
          │                  │                  │
          │                  │                  │
          ▼                  ▼                  ▼
        Wazuh             AI VM             OT Systems
          │
          │
          └──────────────┐
                         │
                         ▼
                     VLAN 50
                    RED TEAM
                         │
                         ▼
                  Testing Targets
