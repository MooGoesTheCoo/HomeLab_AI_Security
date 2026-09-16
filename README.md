# 🛠️ Configuration

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [🛠️ Configuration](../../tree/configuration) | [🗺️ Roadmap](../../tree/roadmap)

[🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery) | [📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# ⚙️ Configuration Management

This section documents the configuration standards and current configuration baseline for the homelab.

The purpose of this page is to maintain a known configuration state and provide a reference when making future changes.

The homelab should be configured deliberately rather than changing multiple components at once without documentation.

---

# 🎯 Configuration Objectives

The configuration approach is designed to provide:

- A known baseline
- Repeatable configuration
- Documented changes
- Clear separation between current and planned configuration
- Easier troubleshooting
- Easier disaster recovery
- Consistent security controls
- Minimal unnecessary changes to the Proxmox host
- A configuration that can eventually be rebuilt from documentation

---

# 📌 Configuration Status

The following status convention is used throughout this documentation.

| Status | Meaning |
|---|---|
| 🟢 Confirmed | Verified on the current system |
| 🟡 Planned | Agreed design but not implemented |
| 🔵 In Progress | Currently being configured or tested |
| 🔴 Not Started | Required but work has not begun |
| ⚠️ Requires Verification | Information still needs to be confirmed |

---

# 🖥️ Proxmox Host Baseline

The current virtualisation host is:

| Item | Current Configuration | Status |
|---|---|---|
| Hostname | `pve` | 🟢 Confirmed |
| Platform | Proxmox VE | 🟢 Confirmed |
| Server | HP ProLiant DL380p Gen8 | 🟢 Confirmed |
| Architecture | `x86_64` | 🟢 Confirmed |
| CPU | 2 × Intel Xeon E5-2650 v2 | 🟢 Confirmed |
| Physical Cores | 16 | 🟢 Confirmed |
| Logical CPUs | 32 | 🟢 Confirmed |
| NUMA Nodes | 2 | 🟢 Confirmed |
| RAM Installed | 256 GB | 🟢 Confirmed |
| Linux RAM Reported | ~220 GiB | 🟢 Confirmed |
| Swap | 8 GiB | 🟢 Confirmed |
| Active Network Interface | `nic7` | 🟢 Confirmed |
| Proxmox Bridge | `vmbr0` | 🟢 Confirmed |
| Management IP | `192.168.0.100/24` | 🟢 Confirmed |
| Gateway | `192.168.0.1` | 🟢 Confirmed |
| RAID Controller | HP Smart Array P420i | 🟢 Confirmed |
| RAID Driver | `hpsa` | 🟢 Confirmed |
| Logical Storage | ~1.6 TB | 🟢 Confirmed |
| GPU | Tesla P40 | 🟡 Planned |

---

# 🌐 Current Network Configuration

The current Proxmox network is intentionally documented before VLAN implementation.

```text
Ubiquiti UX7
     │
     │
     ▼
192.168.0.0/24
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
 Proxmox Host
