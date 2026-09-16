# 🖥️ Hardware Inventory

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🛠️ Configuration](../../tree/configuration)

[🗺️ Roadmap](../../tree/roadmap) | [🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery)

[📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Purpose

This page is the authoritative hardware inventory for the homelab.

It documents the **physical hardware that has been confirmed**, together with hardware that is planned or still requires discovery.

The objective is to avoid making assumptions about the server configuration.

```text
| Category               | Current State                |
| ---------------------- | ---------------------------- |
| Server                 | 🟢 HP ProLiant DL380p Gen8   |
| CPU                    | 🟢 2 × Intel Xeon E5-2650 v2 |
| Physical Cores         | 🟢 16                        |
| Logical CPUs           | 🟢 32                        |
| RAM                    | 🟢 256 GB                    |
| Storage                | 🟢 ~1.6 TB logical           |
| RAID Controller        | 🟢 HP Smart Array P420i      |
| RAID                   | 🟢 RAID-5                    |
| RAID Driver            | 🟢 `hpsa`                    |
| Network Interfaces     | 🟢 10 detected               |
| Active NIC             | 🟢 `nic7`                    |
| Proxmox Bridge         | 🟢 `vmbr0`                   |
| Management IP          | 🟢 `192.168.0.100/24`        |
| Gateway                | 🟢 `192.168.0.1`             |
| iLO                    | 🟢 Present                   |
| Tesla P40              | 🟡 Planned                   |
| Second P40             | 🔴 Future option             |
| PCIe Layout            | 🟡 Being verified            |
| PSU Configuration      | 🟡 TBD                       |
| Cooling                | 🟡 TBD                       |
| Physical Drive Details | 🟡 Being verified            |
