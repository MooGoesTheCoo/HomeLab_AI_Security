# 💾 Backup & Disaster Recovery

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🛠️ Configuration](../../tree/configuration)

[🗺️ Roadmap](../../tree/roadmap) | [🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery)

[📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Purpose

This page documents the backup and disaster recovery strategy for the homelab.

The objective is to ensure that the environment can be recovered after:

- Proxmox failure
- VM failure
- Container failure
- Storage failure
- Configuration mistakes
- Accidental deletion
- Hardware failure
- Network configuration failure
- Security incidents
- Major system rebuilds

The backup strategy will be designed around **recoverability**, not simply keeping copies of data.

---

# ⚠️ Current Status

| Component | Status |
|---|---|
| Proxmox host | 🟢 Operational |
| Proxmox storage | 🟢 Operational |
| Current storage | 🟢 ~1.6 TB logical volume |
| RAID controller | 🟢 HP Smart Array P420i |
| Current RAID level | 🟢 RAID-5 |
| Proxmox backup target | 🟡 Not yet defined |
| VM backup schedule | 🟡 Planned |
| Container backup schedule | 🟡 Planned |
| Configuration backup | 🟡 Planned |
| Off-host backup | 🟡 Planned |
| Off-site backup | 🟡 Planned |
| Restore testing | 🟡 Planned |
| Disaster recovery procedure | 🟡 Planned |
| Recovery priority matrix | 🟡 Planned |

---

# 🏗️ Current Storage Architecture

The Proxmox host currently presents approximately 1.6 TB of storage through the HP Smart Array P420i.

Current operating-system view:

```text
HP DL380p Gen8
        │
        ▼
HP Smart Array P420i
        │
        ▼
Logical Volume
        │
        ▼
~1.6 TB
        │
        ├── pve-root      ~96 GB
        ├── pve-swap       8 GB
        └── pve-data      ~1.5 TB
