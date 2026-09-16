# ⚙️ Proxmox

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🛠️ Configuration](../../tree/configuration)

[🗺️ Roadmap](../../tree/roadmap) | [🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery)

[📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Purpose

This page documents the Proxmox VE configuration and architecture for the homelab.

Proxmox is the virtualisation layer between the physical HP DL380p Gen8 hardware and the virtual machines and containers that will provide the homelab services.

The objective is to build Proxmox in a controlled, documented and reproducible manner.

```text
┌─────────────────────────────────────────────┐
│              HP DL380p Gen8                 │
│                                             │
│  2 × Intel Xeon E5-2650 v2                  │
│  16 Physical Cores / 32 Logical CPUs       │
│  256 GB RAM                                 │
│                                             │
│  P420i RAID-5                               │
│  ~1.6 TB Logical Storage                   │
│                                             │
│  10 × Network Interfaces                   │
│                                             │
├─────────────────────────────────────────────┤
│                                             │
│                 Proxmox VE                  │
│                                             │
├─────────────────────────────────────────────┤
│                                             │
│  Virtual Machines                           │
│  Containers                                 │
│  Virtual Networking                         │
│  Storage                                    │
│  GPU Passthrough                            │
│                                             │
└─────────────────────────────────────────────┘
