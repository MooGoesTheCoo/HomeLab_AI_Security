# 📚 Homelab Documentation

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [🛠️ Configuration](../../tree/configuration) | [🗺️ Roadmap](../../tree/roadmap)

[🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery) | [📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Purpose

This page defines how the homelab project is documented.

The objective is to ensure that the environment can be:

- Understood
- Built
- Tested
- Troubleshot
- Rebuilt
- Expanded
- Audited

without relying on undocumented knowledge.

The documentation should reflect the **actual state of the homelab**, not assumptions about what has been or will be installed.

---

# 📌 Documentation Principles

The project follows these principles:

### 1. Document the actual environment

Hardware and configuration information should be based on verified output wherever possible.

Examples:

```text
lscpu
free -h
lsblk
lspci
ip -br link
ip -br addr
cat /etc/network/interfaces
