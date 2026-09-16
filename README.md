# 🎮 GPU

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🛠️ Configuration](../../tree/configuration)

[🗺️ Roadmap](../../tree/roadmap) | [🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery)

[📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Purpose

This page documents the GPU infrastructure for the homelab.

The primary purpose of the GPU is to provide hardware acceleration for the **Home AI** environment running on the HP ProLiant DL380p Gen8.

The GPU design must account for:

- PCIe slot availability
- PCIe bandwidth
- GPU passthrough
- Power requirements
- Server cooling
- Physical clearance
- Proxmox compatibility
- NVIDIA driver support
- AI workload requirements
- Future GPU expansion

---

# 🖥️ GPU Host

The GPU will be installed in the primary homelab server.

```text
Server:
HP ProLiant DL380p Gen8

Hypervisor:
Proxmox VE

Hostname:
pve
