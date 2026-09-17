<div align="center">

<img src="assets/moogoesthecoo-logo.png" alt="MooGoesTheCoo Homelab Logo" width="500">

# 🐮 MooGoesTheCoo — HomeLab AI & Security

### Enterprise Hardware • Proxmox • Networking • Cybersecurity • OT/ICS • Local AI

**Build it. Break it. Learn it. Secure it.**

</div>

---

## 🏠 About This Project

This repository documents the build of my personal homelab.

The project brings together:

- 🖥️ Enterprise server hardware
- ⚙️ Proxmox virtualisation
- 🌐 Managed networking and VLAN segmentation
- 🛡️ Cybersecurity and security monitoring
- 🔎 Wazuh
- 🤖 Local AI and Home AI workloads
- 🎮 NVIDIA Tesla P40 GPU acceleration
- 🧪 Security testing and attack simulation
- 🏭 OT/ICS learning and experimentation
- 💾 Storage, backup and recovery
- 📊 Infrastructure monitoring
- ⚡ Automation

The goal is not simply to build a collection of virtual machines.

The goal is to build an environment where I can **learn, experiment, break things, investigate what happened, rebuild them and understand the technology behind them.**

This is a real homelab built around physical enterprise hardware and progressively developed through testing and experimentation.

The project is a **work in progress**.

Things will change.

Things will break.

Some components will probably be rebuilt.

That is part of the learning process.

---

# 🧭 Project Navigation

| Area | Documentation |
|---|---|
| 🏠 Project Home | [README](../../) |
| 🏗️ Architecture | [Architecture](../../tree/architecture) |
| 🌐 Networking | [Networking](../../tree/networking) |
| 🔀 VLAN & Segmentation | [VLAN & Network Segmentation](../../tree/VLAN-%26-Network-Segmentation) |
| ⚙️ Proxmox | [Proxmox](../../tree/proxmox) |
| 🖥️ Hardware | [Hardware Inventory](../../tree/hardware-inventory) |
| 🛠️ Configuration | [Configuration](../../tree/configuration) |
| 🗺️ Roadmap | [Roadmap](../../tree/roadmap) |
| 🚀 Deployment | [Deployment](../../tree/deployment) |
| 🔐 Access Management | [Access Management](../../tree/access-management) |
| 🧪 Testing Lab | [Testing Lab](../../tree/testing-lab) |
| 🏭 OT/ICS | [OT/ICS](../../tree/ot-ics) |
| 📚 Documentation | [Documentation](../../tree/documentation) |
| 💾 Backup & Disaster Recovery | [Backup & DR](../../tree/backup-disaster-recovery) |
| 📊 Monitoring | [Monitoring](../../tree/monitoring) |
| 🛡️ Cybersecurity | [Cybersecurity](../../tree/cybersecurity) |
| 🤖 Home AI | [Home AI](../../tree/home-ai) |
| 🎮 GPU | [GPU](../../tree/gpu) |
| 🖥️ Virtual Machines | [Virtual Machines](../../tree/virtual-machines) |
| 💽 Storage | [Storage](../../tree/storage) |
| 🏗️ Infrastructure | [Infrastructure](../../tree/infrastructure) |

---

# 🎯 Project Objectives

The homelab is being developed around several main objectives.

### 1. Learn

Build practical experience with technologies used in real-world infrastructure, cybersecurity, virtualisation, networking and OT environments.

### 2. Experiment

Create isolated environments where new technologies can be tested without putting the normal home network at risk.

### 3. Generate Real Telemetry

Create realistic systems, workloads and security activity that produce logs and events which can then be investigated.

### 4. Build Defensive Security Skills

Use the environment to practise:

- Security monitoring
- Detection engineering
- Incident investigation
- Log analysis
- Threat hunting
- Endpoint monitoring
- Network security
- SIEM operations
- Purple-team exercises

### 5. Learn OT/ICS Security

Build a separate environment for learning how operational technology and industrial control systems differ from traditional IT environments.

### 6. Run AI Locally

Develop a local AI environment capable of running models and AI applications without relying entirely on cloud services.

### 7. Automate

Where practical, automate deployment, configuration, monitoring and repeatable tasks.

---

# 🏗️ Core Infrastructure

The physical foundation of the project is an **HP ProLiant DL380p Gen8** server running Proxmox VE.

### Current Server

| Component | Specification |
|---|---|
| Server | HP ProLiant DL380p Gen8 |
| Hypervisor | Proxmox VE |
| CPU | 2 × Intel Xeon E5-2650 v2 |
| Physical Cores | 16 |
| Logical CPUs | 32 |
| RAM | 256 GB |
| Storage | ~1.6 TB |
| Storage Controller | HP Smart Array P420i |
| Storage Configuration | RAID-5 |
| Network Interfaces | Multiple onboard/server NICs |
| Management | HP iLO |
| Planned GPU | NVIDIA Tesla P40 24 GB |

The server provides the compute and virtualisation platform for the majority of the lab.

➡️ **[View Infrastructure](../../tree/infrastructure)**

➡️ **[View Hardware Inventory](../../tree/hardware-inventory)**

➡️ **[View Proxmox Configuration](../../tree/proxmox)**

---

# 🌐 Network Architecture

The network is being developed around a **Ubiquiti UX7**, managed switching and VLAN-based segmentation.

The existing Proxmox host currently operates on:

```text
Proxmox
    │
    └── nic7
          │
          └── vmbr0
                │
                └── 192.168.0.100/24
