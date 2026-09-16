# 🏠 HomeLab AI & Security

Welcome to my AI driven & designed homelab. This build is designed built and coded mostly by AI (ChatGPT)
I have signed up on a monthly basis to deliver this project. All being well it wont be the fourth road bridge of projects

From here on out, where possible, the pages and actual build will be created by AI (me doing the copy / pasting for the best part)


Regards..





This is a project I'm building to bring together **virtualisation, networking, cybersecurity and local AI** into one environment.

The idea is pretty simple:

Take some enterprise hardware I obtained when it was being binned, put it to work, and build a home environment where I can learn, experiment, test things and actually understand how all the different pieces fit together.

It's a work in progress.

Things will change.

Things will break.

Some things will probably be rebuilt several times.

That's part of the project.

---

# 🧭 Project Overview

The homelab is being built around a central **Proxmox VE** server with managed networking, dedicated GPU resources and a collection of virtual machines and containers.

The environment will eventually provide separate areas for:

- 🖥️ Infrastructure
- ⚙️ Proxmox virtualisation
- 🌐 Networking
- 💾 Storage and backups
- 🤖 Home AI
- 🎮 GPU workloads
- 🛡️ Cybersecurity
- 📊 SIEM / monitoring
- 🧪 Security testing
- ⚡ Automation

Rather than putting everything into one huge document, each part of the build has its own branch.

---

# 🗺️ Build Sections

## 🖥️ Infrastructure

The physical foundation of the homelab.

This section covers the server hardware, physical layout, iLO management, hardware upgrades and the overall architecture.

➡️ **[Open Infrastructure](https://github.com/MooGoesTheCoo/HomeLab_AI_Security/tree/infrastructure)**

---

## ⚙️ Proxmox

The virtualisation platform running the lab.

This section covers the Proxmox installation, configuration, networking, storage, VM management and general host configuration.

➡️ **[Open Proxmox](https://github.com/MooGoesTheCoo/HomeLab_AI_Security/tree/proxmox)**

---

## 🌐 Networking

The network that ties everything together.

This includes the Ubiquiti UX7, managed switching, VLANs, firewalling, network segmentation and management networks.

➡️ **[Open Networking](https://github.com/MooGoesTheCoo/HomeLab_AI_Security/tree/networking)**

---

## 💾 Storage & Backups

Everything related to storing the lab's data.

This section will cover disks, storage configuration, VM storage, backups, snapshots and recovery.

➡️ **[Open Storage](https://github.com/MooGoesTheCoo/HomeLab_AI_Security/tree/storage)**

---

## 🖥️ Virtual Machines & Containers

The systems running inside Proxmox.

This section documents the VMs and containers used throughout the lab, including their purpose, resources and configuration.

➡️ **[Open Virtual Machines](https://github.com/MooGoesTheCoo/HomeLab_AI_Security/tree/virtual-machines)**

---

# 🤖 Home AI

One of the main goals of the project is to build a local AI environment.

The aim is to run AI workloads locally using dedicated GPU resources rather than having everything depend on cloud services.

This section will cover:

- Local LLMs
- AI services
- Model management
- GPU acceleration
- AI applications
- Private document processing
- Automation
- Home AI experiments

➡️ **[Open Home AI](https://github.com/MooGoesTheCoo/HomeLab_AI_Security/tree/home-ai)**

---

# 🎮 GPU

The GPU side of the project.

The current plan includes NVIDIA Tesla P40 hardware for local AI workloads.

This section will document:

- Tesla P40 installation
- Power requirements
- Cooling
- PCIe configuration
- Proxmox GPU passthrough
- Driver installation
- CUDA
- GPU testing
- Adding additional GPUs

➡️ **[Open GPU](https://github.com/MooGoesTheCoo/HomeLab_AI_Security/tree/gpu)**

---

# 🛡️ Cybersecurity Lab

A dedicated environment for cybersecurity learning, testing and experimentation.

The idea is to have systems that can generate realistic security telemetry and allow defensive technologies to be tested in a controlled environment.

This section will eventually include:

- Windows systems
- Linux systems
- Security monitoring
- Endpoint telemetry
- Detection engineering
- Attack simulation
- Purple-team testing
- SOC tooling

➡️ **[Open Cybersecurity](https://github.com/MooGoesTheCoo/HomeLab_AI_Security/tree/cybersecurity)**

---

# 🔎 Wazuh

Wazuh will be the **permanent SIEM/security monitoring platform** for the homelab.

This section will document the Wazuh deployment and how it integrates with the rest of the environment.

It will cover:

- Wazuh server
- Agents
- Windows monitoring
- Linux monitoring
- File integrity monitoring
- Vulnerability detection
- Security events
- Detection rules
- Dashboards
- Alerting
- Testing

➡️ **[Open Wazuh](https://github.com/MooGoesTheCoo/HomeLab_AI_Security/tree/wazuh)**

---

# 📊 Monitoring

Keeping an eye on the infrastructure.

This section will document the tools used to monitor:

- Proxmox
- VMs
- Containers
- CPU
- RAM
- Storage
- Network
- GPU
- Security events
- System health

➡️ **[Open Monitoring](https://github.com/MooGoesTheCoo/HomeLab_AI_Security/tree/monitoring)**

---

# ⚡ Automation

The less I have to configure manually, the better.

This section contains scripts and automation used to deploy, configure and maintain the lab.

Possible areas include:

- PowerShell
- Bash
- Python
- Proxmox automation
- VM deployment
- Configuration
- Backups
- Monitoring
- Security testing

➡️ **[Open Automation](https://github.com/MooGoesTheCoo/HomeLab_AI_Security/tree/automation)**

---

# 📚 Documentation

The general documentation area.

This is where I'll keep information that doesn't naturally belong to one of the other sections.

➡️ **[Open Documentation](https://github.com/MooGoesTheCoo/HomeLab_AI_Security/tree/documentation)**

---

# 🏗️ High-Level Architecture

```text
                         INTERNET
                            │
                            ▼
                    ┌───────────────┐
                    │  Ubiquiti UX7 │
                    └───────┬───────┘
                            │
                            ▼
                    ┌───────────────┐
                    │ Managed Switch│
                    └───────┬───────┘
                            │
              ┌─────────────┼─────────────┐
              │             │             │
              ▼             ▼             ▼
        Management      Home Network    Lab Network
              │                           │
          ┌───┴───┐                 ┌─────┴─────┐
          │  iLO  │                 │  Proxmox  │
          └───────┘                 └─────┬─────┘
                                          │
                         ┌────────────────┼────────────────┐
                         │                │                │
                         ▼                ▼                ▼
                       VMs            Containers       Home AI
                         │                                 │
                         │                           ┌─────▼─────┐
                         │                           │ Tesla P40 │
                         │                           └───────────┘
                         │
                  ┌──────▼──────┐
                  │ Cybersecurity│
                  │     Lab      │
                  └──────┬──────┘
                         │
                    ┌────▼────┐
                    │  Wazuh  │
                    │   SIEM   │
                    └─────────┘
