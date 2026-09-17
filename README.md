# 🐮 MooGoesTheCoo — HomeLab AI & Security

<div align="center">

<img src="assets/moogoesthecoo-logo.png" alt="MooGoesTheCoo Homelab Logo" width="500">

### Enterprise Hardware • Proxmox • Networking • Cybersecurity • OT/ICS • Local AI

**Build it. Break it. Learn it. Secure it.**

</div>

---

# 🤖 The Experiment

This project has a slightly different objective from a normal homelab project.

The main question I am trying to answer is:

> **How much of a real-world homelab can AI actually specify, design, document and help build from start to finish?**

The intention is to use AI **heavily** throughout this project to see whether it can handle most, if not all, aspects of designing and building the lab.

That includes:

- 🏗️ Architecture
- 🖥️ Hardware specification
- ⚙️ Proxmox
- 🌐 Networking
- 🔀 VLANs and segmentation
- 🔐 Security architecture
- 🧪 Testing environments
- 🛡️ Cybersecurity
- 🔎 SIEM and monitoring
- 🏭 OT/ICS
- 🤖 Home AI
- 🎮 GPU configuration
- 💾 Storage
- 💾 Backup and recovery
- 🚀 Deployment
- ⚡ Automation
- 📚 Documentation
- 🔧 Troubleshooting
- 🧪 Testing and validation

The basic idea is:

**AI proposes, specifies, explains and documents.**

**I build it, configure it, test it and report what actually happens.**

This means the repository is not simply documentation for a homelab.

It is also a record of an experiment to see how far AI can actually take a real technical project.

---

# 🧠 AI-Assisted Development

AI is being used heavily to help build, develop and document this project.

AI is being used for:

- Architecture design
- Technical research
- Hardware planning
- Network design
- Configuration
- Scripting
- Automation
- Troubleshooting
- Documentation
- Testing
- Learning
- Reviewing proposed designs
- Planning future stages

The majority of the technical documentation and development guidance is being created with significant assistance from AI.

However, this is a **real physical homelab**.

The hardware is real.

The network is real.

The configurations are real.

The testing is real.

And when something doesn't work, it has to be fixed in the real world.

AI doesn't get to hide behind a nice-looking diagram.

If AI gets something wrong, it becomes part of the experiment.

If a configuration fails, it gets investigated.

If a design needs changing, it gets changed.

If an AI-generated solution is completely ridiculous, it gets called out.

---

# 🌉 The Fourth Road Bridge Test

There is one additional objective.

I want to see whether AI can help build this project **without turning it into the Fourth Road Bridge**.

In other words:

> **Can AI design and build something technically capable without massively over-engineering it?**

The solutions need to be:

- Practical
- Affordable
- Secure
- Maintainable
- Reproducible
- Appropriate for the available hardware
- Understandable
- Actually deployable

The objective is to build a working homelab.

Not a theoretical enterprise architecture that requires a team of 40 engineers to operate.

If the project starts heading towards becoming another Fourth Road Bridge, that is something that should be identified and corrected.

---

# 🧑‍💻 My Role

AI is doing a significant amount of the thinking, planning and documentation.

My role is to:

- Obtain and install the hardware
- Perform the physical build
- Execute configurations
- Run commands and scripts
- Test the results
- Validate proposed solutions
- Provide real-world feedback
- Troubleshoot problems
- Make physical changes
- Decide what gets deployed

Essentially:

> **AI can design the bridge. I'm the one standing underneath it when we test it.**

That is an important part of the experiment.

---

# 🏠 About The Project

This project brings together:

- Virtualisation
- Networking
- Cybersecurity
- OT/ICS
- Local AI
- GPU computing
- Monitoring
- Automation
- Security testing

The project is being built around enterprise hardware that was obtained when it was being discarded.

The intention is to give that hardware a second life while creating a practical environment for learning, experimentation and testing.

This is a **work in progress**.

Things will change.

Things will break.

Things will probably be rebuilt.

That's part of the project.

---

# 🧭 Project Navigation

The project is split into individual sections so that each part can be developed and documented independently.

## 🏗️ Infrastructure

The physical foundation of the homelab.

This covers:

- Server hardware
- Physical infrastructure
- iLO
- Hardware upgrades
- Physical architecture

➡️ **[Open Infrastructure](../../tree/infrastructure)**

---

## ⚙️ Proxmox

The virtualisation platform running the lab.

This covers:

- Proxmox installation
- Host configuration
- Networking
- Storage
- VM management
- Virtualisation

➡️ **[Open Proxmox](../../tree/proxmox)**

---

## 🌐 Networking

The network that ties the entire environment together.

This covers:

- Ubiquiti UX7
- Managed switching
- Network design
- VLANs
- Routing
- Firewalling
- Network segmentation
- Management networking

➡️ **[Open Networking](../../tree/networking)**

---

## 🔀 VLAN & Network Segmentation

The security boundaries between the different areas of the homelab.

Planned environments include:

- Management
- Infrastructure
- Security
- Home AI
- OT/ICS
- Testing
- User
- IoT
- Guest

➡️ **[Open VLAN & Network Segmentation](../../tree/VLAN-%26-Network-Segmentation)**

---

## 💾 Storage

Everything relating to storage within the homelab.

This covers:

- Proxmox storage
- VM storage
- AI model storage
- Capacity
- Storage planning

➡️ **[Open Storage](../../tree/storage)**

---

## 💾 Backup & Disaster Recovery

Backup and recovery planning for the environment.

This covers:

- Backups
- Recovery
- Snapshots
- Disaster recovery
- Recovery testing

➡️ **[Open Backup & Disaster Recovery](../../tree/backup-disaster-recovery)**

---

## 🖥️ Virtual Machines

The systems running inside Proxmox.

This section documents:

- VM purpose
- CPU allocation
- RAM allocation
- Storage
- Networking
- Configuration
- Deployment

➡️ **[Open Virtual Machines](../../tree/virtual-machines)**

---

# 🤖 Home AI

One of the major objectives is to build a local AI environment.

The aim is to run AI workloads locally rather than having everything depend on cloud services.

Home AI will cover:

- Local LLMs
- AI services
- Model management
- GPU acceleration
- AI applications
- Document processing
- Automation
- AI experimentation
- AI-assisted projects

➡️ **[Open Home AI](../../tree/home-ai)**

---

# 🎮 GPU

The GPU environment supporting local AI workloads.

The current plan includes NVIDIA Tesla P40 hardware.

This section covers:

- Tesla P40 installation
- Power
- Cooling
- PCIe configuration
- GPU passthrough
- NVIDIA drivers
- CUDA
- GPU testing
- Additional GPU expansion

➡️ **[Open GPU](../../tree/gpu)**

---

# 🛡️ Cybersecurity

The cybersecurity environment provides a controlled environment for learning and experimentation.

This will allow security activity to be generated deliberately and then investigated.

Areas include:

- Windows security
- Linux security
- Endpoint telemetry
- Security monitoring
- Detection engineering
- Threat hunting
- Attack simulation
- Purple-team testing
- SOC workflows
- IOC generation

➡️ **[Open Cybersecurity](../../tree/cybersecurity)**

---

# 🔎 Wazuh

Wazuh is the permanent SIEM/security monitoring platform planned for the homelab.

It will provide central security visibility across the environment.

This includes:

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

➡️ **[Open Wazuh / Cybersecurity](../../tree/cybersecurity)**

---

# 📊 Monitoring

Monitoring provides visibility across the infrastructure.

This covers:

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

➡️ **[Open Monitoring](../../tree/monitoring)**

---

# 🧪 Testing Lab

A controlled environment for testing systems and security technologies.

The testing environment will be used to:

- Generate telemetry
- Test detections
- Perform controlled attacks
- Investigate events
- Validate security controls
- Break and rebuild systems

➡️ **[Open Testing Lab](../../tree/testing-lab)**

---

# 🏭 OT/ICS

A separate environment for learning Operational Technology and Industrial Control Systems.

The OT/ICS environment will focus on:

- Industrial networking
- PLC concepts
- SCADA
- HMI
- Industrial protocols
- OT monitoring
- OT security
- Network segmentation
- Security testing

The OT environment will remain isolated from the normal home environment.

➡️ **[Open OT/ICS](../../tree/ot-ics)**

---

# 🔐 Access Management

Access controls for the homelab.

This covers:

- Administrative access
- Proxmox access
- iLO access
- VM access
- Service access
- Authentication
- Least privilege
- Management access

➡️ **[Open Access Management](../../tree/access-management)**

---

# 🚀 Deployment

The deployment section documents how systems are actually installed and brought into service.

This includes:

- VM deployment
- Service installation
- Network configuration
- Security configuration
- GPU deployment
- Testing
- Validation

➡️ **[Open Deployment](../../tree/deployment)**

---

# 🛠️ Configuration

Configuration documentation for the environment.

The aim is that the homelab can be understood and rebuilt rather than relying on undocumented manual changes.

➡️ **[Open Configuration](../../tree/configuration)**

---

# ⚡ Automation

The less that needs to be configured manually, the better.

Automation will be used where it provides a practical benefit.

Potential areas include:

- PowerShell
- Bash
- Python
- Proxmox automation
- VM deployment
- Configuration
- Backups
- Monitoring
- Security testing

➡️ **[Open Automation](../../tree/configuration)**

---

# 📚 Documentation

General project documentation that doesn't naturally belong elsewhere.

This also provides supporting information for the overall project.

➡️ **[Open Documentation](../../tree/documentation)**

---

# 🗺️ Roadmap

The project is being developed progressively.

The roadmap tracks what has been:

- Completed
- Tested
- In progress
- Planned
- Deferred

➡️ **[Open Roadmap](../../tree/roadmap)**

---

# 🏗️ Architecture

The overall architecture brings all of the individual components together.

➡️ **[Open Architecture](../../tree/architecture)**

---

# 📐 High-Level Architecture

```text
                         INTERNET
                            │
                            ▼
                    ┌───────────────┐
                    │ Ubiquiti UX7  │
                    │    Gateway    │
                    └───────┬───────┘
                            │
                            ▼
                    ┌───────────────┐
                    │ Managed Switch│
                    └───────┬───────┘
                            │
                      802.1Q Trunk
                            │
                            ▼
                    ┌───────────────┐
                    │    Proxmox    │
                    │    DL380p     │
                    └───────┬───────┘
                            │
                     VLAN-aware vmbr0
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                   │
        ▼                   ▼                   ▼
   Management         Infrastructure        Security
    VLAN 10              VLAN 20             VLAN 30
        │                   │                   │
       iLO              Services              Wazuh
                                               │
                                               ▼
                                        Security Telemetry

        ┌───────────────────┼───────────────────┐
        │                   │                   │
        ▼                   ▼                   ▼
     Home AI             OT / ICS           Testing
     VLAN 40             VLAN 50             VLAN 60
        │                   │                   │
        ▼                   ▼                   ▼
   AI Services        OT Environment       Test Systems
        │
        ▼
    Tesla P40

                    ┌─────────────────┐
                    │  User Network   │
                    │     VLAN 70     │
                    └─────────────────┘

                    ┌─────────────────┐
                    │    IoT VLAN     │
                    │     VLAN 80     │
                    └─────────────────┘

                    ┌─────────────────┐
                    │   Guest VLAN    │
                    │     VLAN 90     │
                    └─────────────────┘
