# 🖥️ Hardware Inventory

[🏠 Home](../) | [🏗️ Architecture](../architecture) | [🌐 Networking](../networking) | [🔀 VLANs](../vlans) | [⚙️ Proxmox](../proxmox) | [🖥️ Hardware](./) | [🛠️ Configuration](../configuration)

[🗺️ Roadmap](../roadmap) | [🚀 Deployment](../deployment) | [🔐 Access Management](../access-management) | [🧪 Testing Lab](../testing-lab) | [🏭 OT/ICS](../ot-ics) | [📚 Documentation](../documentation) | [💾 Backup & DR](../backup-dr)

[📊 Monitoring](../monitoring) | [🛡️ Cybersecurity](../cybersecurity) | [🤖 Home AI](../home-ai) | [🎮 GPU](../gpu) | [🖥️ Virtual Machines](../virtual-machines) | [💽 Storage](../storage) | [🏗️ Infrastructure](../infrastructure)

---

# 📋 Overview

This page documents the physical hardware that forms the foundation of the **MooGoesTheCoo HomeLab AI & Security** project.

The inventory is maintained as the project develops so that the documentation reflects the **actual hardware owned and used by the lab**, rather than only equipment originally planned.

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
| GPU | NVIDIA Tesla P40 — planned |
| Remote Management | HP iLO |
| Network Interfaces | Multiple onboard/server NICs |
| Current Proxmox Management IP | `192.168.0.100/24` |
| Current Gateway | `192.168.0.1` |

### Planned Role

The DL380p Gen8 is the primary compute platform for the homelab.

It will host the majority of the project's virtualised environments, including:

- Core infrastructure
- Blue Team / SOC systems
- Wazuh
- Red Team systems
- AI infrastructure
- Home AI
- Windows and Linux test systems
- OT/ICS laboratory systems
- Security testing environments

Future NVIDIA Tesla P40 GPU hardware is planned for local AI workloads and GPU experimentation.

---

# 🌐 Network Hardware

## Ubiquiti UniFi Switch Lite 8 PoE

> 🟢 **RECEIVED — 1 × Ubiquiti USW-Lite-8-PoE-UK**

The UniFi Switch Lite 8 PoE has now been received and will become the primary managed access switch for the physical homelab network.

It will connect the:

- Ubiquiti UX7
- HP DL380p Gen8
- Main PC
- Secondary PC
- iLO management
- Future homelab devices

The switch will also provide the Layer-2 foundation for the planned VLAN and network-segmentation architecture.

### Purchase Information

| Item | Details |
|---|---|
| Manufacturer | Ubiquiti |
| Model | UniFi Switch Lite 8 PoE |
| UK Model | USW-Lite-8-PoE-UK |
| Quantity | 1 |
| Purchase Price | £85.00 |
| Status | 🟢 Received — awaiting deployment/configuration |
| Role | Primary managed access switch |

### Technical Specification

| Specification | Details |
|---|---|
| Ethernet Ports | 8 × 1 GbE RJ45 |
| PoE Ports | 4 × PoE+ |
| Total PoE Budget | 52 W |
| VLAN Support | Yes |
| Management | UniFi Network |
| Switching Role | Managed Layer-2 access switch |
| Planned Location | Homelab network |

### Why 1 GbE is being used

The homelab currently does not require a full 10 GbE switching infrastructure.

The primary workstation is expected to be responsible for approximately **95% of interactive access to the lab**, including:

- Proxmox management
- Wazuh
- AI interfaces
- Home AI
- RDP/SSH
- Security testing
- Lab administration

The DL380p has 10 GbE capability, but the current design prioritises:

**VLAN capability, network segmentation, reliability and cost efficiency over 10 GbE switching.**

A future 2.5/10 GbE upgrade remains possible if high-volume data transfer becomes a requirement.

---

# 🔌 Network Cabling

The following UniFi Ethernet patch cables have been purchased for the homelab network.

## UniFi Patch Cable — 8 m

| Specification | Details |
|---|---|
| Manufacturer | Ubiquiti |
| Product | UniFi Patch Cable |
| Speed Rating | 10 GbE |
| Length | 8 m |
| Quantity | 2 |
| Unit Price | £14.40 |
| Status | 🟢 Received |

### Planned Use

The longer cables will be used for physical connections where equipment is positioned away from the switch, including the main workstation and other future network devices.

---

## UniFi Patch Cable — 5 m

| Specification | Details |
|---|---|
| Manufacturer | Ubiquiti |
| Product | UniFi Patch Cable |
| Speed Rating | 10 GbE |
| Length | 5 m |
| Quantity | 1 |
| Unit Price | £5.60 |
| Status | 🟢 Received |

---

## UniFi Patch Cable — 1 m

| Specification | Details |
|---|---|
| Manufacturer | Ubiquiti |
| Product | UniFi Patch Cable |
| Speed Rating | 10 GbE |
| Length | 1 m |
| Quantity | 1 |
| Unit Price | £3.00 |
| Status | 🟢 Received |

### Cable Note

The 10 GbE rating of the patch cables provides additional capability for future network upgrades.

The current USW-Lite-8-PoE provides 1 GbE Ethernet ports, so the cables do not increase the switch port speed. They provide reusable cabling should the network later be upgraded to higher-speed Ethernet.

---

# 🌐 Current Home Network

The homelab is being introduced alongside the existing home network rather than replacing it.

Current home network subnets:

| Network | Mask | Status |
|---|---|---|
| `192.168.0.0/24` | `/24` | Existing home network |
| `192.168.1.0/24` | `/24` | Primary home network |
| `192.168.2.0/24` | `/24` | Existing home network |
| `192.168.3.0/24` | `/24` | Existing home network |
| `192.168.4.0/24` | `/24` | Existing home network |
| `192.168.5.0/24` | `/24` | Existing home network |

The primary workstation currently operates primarily on:

**`192.168.1.0/24`**

The workstation is currently using WLAN and is planned to move to a wired Ethernet connection as the physical homelab network is deployed.

The existing home networks will remain separate from the dedicated homelab VLANs.

---

# 🔀 Planned Homelab VLAN Architecture

The homelab will use separate VLANs to isolate management, security, AI, OT and testing environments.

| VLAN | Purpose | Planned Subnet |
|---:|---|---|
| 10 | Management | `192.168.10.0/24` |
| 20 | Blue Team / Wazuh | `192.168.20.0/24` |
| 30 | Home AI | `192.168.30.0/24` |
| 40 | OT/ICS | `192.168.40.0/24` |
| 50 | Red Team | `192.168.50.0/24` |
| 60 | Lab Servers | `192.168.60.0/24` |
| 70 | Lab Clients | `192.168.70.0/24` |

These networks are planned and will be introduced progressively as each section of the homelab is built.

The UX7 will provide routing and firewall enforcement between networks, while the USW-Lite-8-PoE will provide managed Layer-2 connectivity.

---

# 🗺️ Planned Physical Network Role

```text
                         INTERNET
                            │
                            ▼
                    ┌──────────────┐
                    │     UX7      │
                    │   Gateway    │
                    │  Firewall    │
                    └──────┬───────┘
                           │
                           │ Ethernet
                           │
                           ▼
                ┌────────────────────┐
                │  USW-Lite-8-PoE    │
                │   Managed Switch   │
                └─────────┬──────────┘
                          │
          ┌───────────────┼────────────────┐
          │               │                │
          ▼               ▼                ▼
       DL380p          Main PC           PC #2
       Proxmox        192.168.1.x
          │
          │ VLAN Trunk
          │
    ┌─────┼──────────────┬──────────────┐
    │     │              │              │
    ▼     ▼              ▼              ▼
   MGMT  BLUE            AI             RED
  VLAN10 VLAN20         VLAN30         VLAN50
    │
    └─────────────────────────────────────┐
                                          │
                                         OT
                                       VLAN40
