# 🌐 Network Overview

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [🛠️ Configuration](../../tree/configuration) | [🗺️ Roadmap](../../tree/roadmap)

[🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery) | [📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🌐 Network Overview

This section documents the physical and logical network architecture of the homelab.

The network is being designed around:

- Ubiquiti UX7
- Managed Ethernet switching
- HP ProLiant DL380p Gen8
- Proxmox VE
- iLO out-of-band management
- VLAN segmentation
- Blue Team infrastructure
- Home AI infrastructure
- OT/ICS laboratory
- Red Team security testing
- Dedicated management networking

The network will initially be built from the existing working configuration and progressively migrated towards the segmented architecture.

---

# 🎯 Network Design Objectives

The network should provide:

- Reliable connectivity for the Proxmox host
- Dedicated management access
- Separation of security environments
- Isolation of OT/ICS systems
- Controlled access between VLANs
- Dedicated Home AI networking
- Controlled Red Team testing
- Blue Team visibility across relevant environments
- A scalable design for additional VMs and physical systems
- Minimal disruption while the network is migrated from the current flat network

---

# 🏠 Current Physical Network

The current network is operating as a flat `192.168.0.0/24` network.

```text
                         INTERNET
                            │
                            │
                            ▼
                     ┌─────────────┐
                     │ Ubiquiti    │
                     │ UX7         │
                     └──────┬──────┘
                            │
                            │
                     CURRENT LAN
                  192.168.0.0/24
                            │
                            ▼
                    ┌─────────────┐
                    │ Proxmox     │
                    │ DL380p G8   │
                    └──────┬──────┘
                           │
                         nic7
                           │
                         vmbr0
                           │
                           ▼
                  192.168.0.100/24
