# 🖥️ Virtual Machines

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🛠️ Configuration](../../tree/configuration)

[🗺️ Roadmap](../../tree/roadmap) | [🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery)

[📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Purpose

This page documents the virtual machine architecture for the homelab.

The objective is to define how workloads will be distributed across the Proxmox host while maintaining:

- Security
- Network segmentation
- Resource isolation
- Monitoring
- Backup capability
- Recovery capability
- Scalability
- Clear workload separation

The virtual machine architecture will evolve as individual services are deployed and tested.

---

# 🖥️ Proxmox Host

All virtual machines will initially run on the primary Proxmox host.

```text
HP ProLiant DL380p Gen8
          │
          ▼
      Proxmox VE
          │
    ┌─────┼──────────────────────────────┐
    │     │              │               │
    ▼     ▼              ▼               ▼
 Infra  Security       Home AI         Testing
  VMs      VMs           VM              VMs
                         │
                         ▼
                    Tesla P40
