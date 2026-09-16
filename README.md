# 🔐 Access Management

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [🛠️ Configuration](../../tree/configuration) | [🗺️ Roadmap](../../tree/roadmap)

[🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery) | [📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Purpose

This page documents how administrative and operational access to the homelab will be controlled.

The objective is to separate:

- Infrastructure management
- Network management
- Security administration
- VM administration
- OT/ICS access
- Red Team access
- Home AI access
- User access

The access model will evolve as VLANs and additional systems are deployed.

---

# 🚦 Current Status

| Area | Current State | Status |
|---|---|---|
| Proxmox management | `192.168.0.100/24` | 🟢 Operational |
| Proxmox hostname | `pve` | 🟢 Confirmed |
| Proxmox web management | Available on current management network | 🟢 Operational |
| Proxmox SSH | Available locally | 🟢 Operational |
| iLO | Present | 🟡 Configuration to be documented |
| Ubiquiti UX7 | Present | 🟡 Configuration to be documented |
| Managed switch | Not yet finalised | 🟡 Planned |
| Management VLAN | VLAN 10 | 🟡 Planned |
| Dedicated management network | Not yet implemented | 🟡 Planned |
| MFA / 2FA | Not yet documented | 🟡 Planned |
| Central authentication | Not yet implemented | 🟡 Planned |
| Privileged account separation | To be implemented | 🟡 Planned |
| OT/ICS access controls | Not yet implemented | 🟡 Planned |
| Red Team isolation | Not yet implemented | 🟡 Planned |

---

# 🖥️ Current Management Access

The current Proxmox management configuration is:

```text
Proxmox Host
    │
    ▼
nic7
    │
    ▼
vmbr0
    │
    ▼
192.168.0.100/24
    │
    ▼
Gateway
192.168.0.1
