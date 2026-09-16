# 📊 Monitoring & Observability

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🛠️ Configuration](../../tree/configuration)

[🗺️ Roadmap](../../tree/roadmap) | [🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery)

[📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Purpose

This page documents the monitoring and observability architecture for the homelab.

The monitoring design will provide visibility across:

- Physical hardware
- Proxmox
- Virtual machines
- Containers
- Network infrastructure
- Security infrastructure
- Wazuh
- OT/ICS systems
- Home AI infrastructure
- Storage
- GPU resources
- System availability
- Security events

The objective is to provide a single documented monitoring architecture while keeping security monitoring separate from general infrastructure monitoring where appropriate.

---

# 🧭 Monitoring Architecture

The planned monitoring architecture is:

```text
                         HOMELAB
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                   │
        ▼                   ▼                   ▼
   Infrastructure       Network             Security
        │                   │                   │
        │                   │                   ▼
        │                   │                 Wazuh
        │                   │                   │
        ▼                   ▼                   ▼
     Proxmox             Network          Security Events
        │                Devices
        │
   ┌────┼────────┐
   │    │        │
   ▼    ▼        ▼
  VMs   CTs     GPU
   │
   ▼
 Applications
