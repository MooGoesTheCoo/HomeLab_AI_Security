# 🏭 OT / ICS Lab

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🛠️ Configuration](../../tree/configuration)

[🗺️ Roadmap](../../tree/roadmap) | [🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery)

[📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Purpose

This page documents the planned OT/ICS environment within the homelab.

The objective is to build a controlled environment that can be used to:

- Learn OT/ICS security
- Simulate industrial environments
- Investigate OT protocols
- Generate realistic OT telemetry
- Test defensive monitoring
- Test SIEM detection
- Test network segmentation
- Perform controlled security exercises
- Develop OT SOC analyst skills
- Integrate OT telemetry with the wider security lab

The OT environment will remain isolated from the normal home network and will be introduced only after the underlying network and security architecture has been implemented.

---

# ⚠️ Current Status

| Component | Status |
|---|---|
| OT/ICS architecture | 🟡 Planned |
| OT VLAN | 🟡 Planned |
| OT firewall policy | 🟡 Planned |
| OT DMZ | 🟡 Planned |
| PLC simulation | 🟡 Planned |
| HMI simulation | 🟡 Planned |
| Engineering workstation | 🟡 Planned |
| SCADA | 🟡 Planned |
| Historian | 🟡 Planned |
| OT network monitoring | 🟡 Planned |
| Wazuh integration | 🟡 Planned |
| OT attack simulation | 🟡 Planned |
| OT detection engineering | 🟡 Planned |

**No OT/ICS systems are currently documented as deployed.**

---

# 🏗️ High-Level OT Architecture

The intended architecture is:

```text
                         HOME / IT NETWORK
                                │
                                │
                         ┌──────▼──────┐
                         │   FIREWALL  │
                         └──────┬──────┘
                                │
                                │ Controlled Traffic
                                ▼
                         ┌─────────────┐
                         │   OT DMZ    │
                         │    VLAN     │
                         └──────┬──────┘
                                │
                         Controlled Access
                                │
                                ▼
                         ┌─────────────┐
                         │ OT FIREWALL │
                         └──────┬──────┘
                                │
                                ▼
                         ┌─────────────┐
                         │  OT NETWORK │
                         │    VLAN     │
                         └──────┬──────┘
                                │
              ┌─────────────────┼─────────────────┐
              │                 │                 │
              ▼                 ▼                 ▼
           PLC /             HMI /          Engineering
         Controller         Operator          Workstation
                           Station
              │                 │                 │
              └─────────────────┼─────────────────┘
                                │
                                ▼
                           SCADA / Server
                                │
                                ▼
                           Historian
