# 🔀 VLAN & Network Segmentation

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🛠️ Configuration](../../tree/configuration)

[🗺️ Roadmap](../../tree/roadmap) | [🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery)

[📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Purpose

This page documents the VLAN and network segmentation architecture for the homelab.

The purpose of segmentation is to separate systems according to their role and security requirements rather than operating the entire environment on a single flat network.

The design will support:

- Infrastructure
- Proxmox management
- iLO management
- Security monitoring
- Home AI
- OT/ICS
- Testing
- User devices
- Future services

The VLAN architecture will be implemented progressively.

**The VLANs and trunking described below are the target design unless explicitly marked as confirmed.**

---

# ⚠️ Current Network State

The network is currently operating on a **single unsegmented management/network configuration**.

Current Proxmox configuration:

```text
Proxmox
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
192.168.0.1
