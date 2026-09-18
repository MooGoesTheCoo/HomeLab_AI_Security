# 🖥️ Hardware Inventory

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🛠️ Configuration](../../tree/configuration)

[🗺️ Roadmap](../../tree/roadmap) | [🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery)

[📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 📋 Overview

This page documents the physical hardware that forms the foundation of the MooGoesTheCoo HomeLab AI & Security project.

The inventory is maintained as the project develops so that the documentation reflects the **actual hardware owned and used by the lab**, rather than only the equipment originally planned.

The project is being built around enterprise hardware combined with consumer and networking equipment.

The objective is to create a practical environment for:

- Virtualisation
- Networking
- Cybersecurity
- Security monitoring
- OT/ICS experimentation
- Local AI
- GPU computing
- Testing
- Automation
- Learning

---

# 🖥️ Main Virtualisation Server

## HP ProLiant DL380p Gen8

| Component | Specification |
|---|---|
| Manufacturer | HP |
| Model | ProLiant DL380p Gen8 |
| Role | Primary virtualisation server |
| Hypervisor | Proxmox VE |
| CPU | 2 × Intel Xeon E5-2650 v2 |
| Physical Cores | 16 |
| Logical CPUs | 32 |
| CPU Base Frequency | 2.60 GHz |
| CPU Maximum Frequency | 3.40 GHz |
| RAM | 256 GB |
| Storage | ~1.6 TB |
| Storage Controller | HP Smart Array P420i |
| Storage Driver | `hpsa` |
| RAID | RAID-5 |
| GPU | NVIDIA Tesla P40 planned |
| Remote Management | HP iLO |
| Network Interfaces | Multiple onboard/server NICs |
| Current Proxmox Management IP | `192.168.0.100/24` |
| Current Gateway | `192.168.0.1` |




## 🆕 New Network Hardware Purchase

### Ubiquiti UniFi Switch Lite 8 PoE

> **🟢 NEW PURCHASE — 1 × Ubiquiti USW-Lite-8-PoE**
>
> This switch has now been purchased and is the first major addition to the physical network infrastructure for this project.
>
> It will become the managed switch connecting the **Ubiquiti UX7, Proxmox DL380p and standalone PCs**, and will provide the switching platform for the planned VLAN and network-segmentation architecture.
>
> **Purchase price: £deleted**
>
> **Status: 🟢 Purchased — awaiting deployment/configuration**

| Specification | Details |
|---|---|
| Manufacturer | Ubiquiti |
| Model | UniFi Switch Lite 8 PoE |
| Model Number | USW-Lite-8-PoE |
| Ports | 8 × 1 GbE RJ45 |
| PoE | 4 × PoE+ |
| Total PoE Budget | 52 W |
| VLAN Support | Yes |
| Role | Core managed access switch for the homelab |
| Status | 🟢 Purchased |
| Purchase Price | deleted |


<img width="1672" height="941" alt="3acc830e-2f6c-4f3d-a2bb-a85d88debf5b" src="https://github.com/user-attachments/assets/c393fce2-d180-4ab5-b15f-c448d494593b" />


### Planned Physical Role

```text
                    INTERNET
                       │
                       ▼
                ┌─────────────┐
                │ Ubiquiti UX7│
                │   Gateway   │
                └──────┬──────┘
                       │
                       │ Ethernet
                       ▼
             ┌────────────────────┐
             │ 🆕 USW-Lite-8-PoE  │
             │  Managed Switch    │
             └─────────┬──────────┘
                       │
             ┌─────────┼─────────┐
             │         │         │
             ▼         ▼         ▼
          DL380p     PC #1     PC #2
         Proxmox
             │
             ▼
       Future VLAN Trunk
             │
       ┌─────┼─────┬─────┬─────┐
       ▼     ▼     ▼     ▼     ▼
      MGMT  INFRA SECURITY AI  TEST
