# 🌐 Network Architecture & Connectivity

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🛠️ Configuration](../../tree/configuration)

[🗺️ Roadmap](../../tree/roadmap) | [🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery)

[📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Purpose

This page documents the physical and logical network architecture of the homelab.

It provides the link between the physical network equipment and the VLAN, Proxmox and security architecture documented elsewhere in the project.

The network is being built in stages.

The current environment is operational on a single LAN, while the final architecture will introduce VLAN segmentation, trunking and controlled inter-VLAN routing.

---

# ⚠️ Current Network Status

The current network is **not yet VLAN segmented**.

The confirmed Proxmox connection is:

```text
HP DL380p Gen8
        │
        │ Physical Ethernet
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
