# Homelab Infrastructure

## Overview

This repository documents the design, deployment and configuration of a virtualised homelab environment based on an HPE ProLiant DL380p Gen8 running Proxmox VE.

The environment is being designed as a segmented laboratory supporting:

- Cybersecurity / SOC training
- Red Team activity simulation
- Blue Team detection and investigation
- SIEM and security telemetry
- OT / ICS security laboratories
- Local AI infrastructure
- Home AI workloads
- Virtual networking and security architecture
- Future GPU-accelerated workloads

The design prioritises network segmentation, controlled inter-zone communication, repeatable testing and infrastructure isolation.

---

# 1. Physical Infrastructure

## 1.1 Server

**Platform**

HPE ProLiant DL380p Gen8

**Hypervisor**

Proxmox VE

**Host operating system**

Debian GNU/Linux 13 (Trixie)

**Architecture**

x86_64

### CPU

- 2 × Intel Xeon E5-2650 v2
- 8 physical cores per CPU
- 16 physical cores total
- 32 logical CPUs
- Hyper-Threading enabled
- Intel VT-x supported
- 2 NUMA nodes

### Memory

- Installed RAM: 256 GB
- Operating system currently reports approximately 220 GiB usable
- Approximately 217 GiB available at the time of assessment

### Storage

Approximately 1.6 TB physical storage is currently installed.

Current storage layout:

    sda
    ├── sda1
    ├── sda2        1 GB EFI
    └── sda3        LVM
        ├── pve-swap       8 GB
        ├── pve-root      96 GB
        └── pve-data       ~1.5 TB

Proxmox currently uses an LVM-thin datastore of approximately 1.5 TB.

---

# 2. PCIe Inventory

Current PCIe devices identified on the server include:

| PCIe Device | Hardware | Function |
|---|---|---|
| 04:00.0 / 04:00.1 | QLogic Fibre Channel HBA | Fibre Channel |
| 03:00.0 / 03:00.1 | Broadcom BCM57810 | 10GbE |
| 07:00.0 - 07:00.3 | Broadcom BCM5719 | 1GbE |
| 21:00.0 - 21:00.3 | Broadcom BCM5719 | 1GbE |
| 01:00.1 | Matrox MGA G200EH | Server graphics / iLO |
| 02:00.0 | HP Smart Array Gen8 | Storage controller |

---

# 3. PCIe Slot Availability

Current server slot information:

| Slot | PCIe Generation | Width | Status |
|---|---|---:|---|
| PCI-E Slot 1 | PCIe Gen3 | x16 | In use |
| PCI-E Slot 2 | PCIe Gen3 | x8 | In use |
| PCI-E Slot 3 | PCIe Gen2 | x4 | Available |
| PCI-E Slot 4 | PCIe Gen3 | x16 | In use |
| PCI-E Slot 5 | PCIe Gen3 | x8 | Available |
| PCI-E Slot 6 | PCIe Gen3 | x8 | Available |

Available slots provide scope for future hardware expansion.

Potential future expansion includes:

- NVIDIA Tesla P40
- Additional GPU
- Additional network adapter
- Additional storage/networking hardware

GPU installation will be validated against the DL380p Gen8 riser, slot, power and thermal requirements before purchase.

---

# 4. Network Interfaces

## 4.1 1GbE

The server contains eight Broadcom BCM5719 Gigabit Ethernet interfaces.

Interfaces:

    nic0
    nic1
    nic2
    nic3

and:

    nic4
    nic5
    nic6
    nic7

`nic7` is currently the active interface used by Proxmox.

---

# 5. 10GbE Network Interfaces

The server contains two Broadcom BCM57810 10GbE interfaces.

Interfaces:

    nic8
    nic9

Both interfaces have been verified using `ethtool`.

Supported link speeds:

- 100 Mbps
- 1 Gbps
- 10 Gbps

Interface type:

    Twisted Pair / RJ45

These interfaces are NOT SFP/SFP+.

Current state:

    nic8
    Link detected: no

    nic9
    Link detected: no

The intention is to use the 10GbE interfaces for the lab infrastructure once the appropriate network switching infrastructure is installed.

---

# 6. Fibre Channel

A QLogic dual-port Fibre Channel HBA is installed.

PCIe devices:

    04:00.0
    04:00.1

The Fibre Channel adapter is currently not part of the primary Ethernet topology.

Potential future uses:

- SAN laboratory
- Fibre Channel training
- Storage networking
- Enterprise storage simulation

---

# 7. Current Network

The current Proxmox management/network configuration is:

    Home LAN
       |
       |
      UX7
       |
       |
     nic7
       |
      vmbr0
       |
       +---- 192.168.0.100/24
              |
              Proxmox

Current Proxmox address:

    192.168.0.100/24

Current network:

    192.168.0.0/24

The existing home network is considered the trusted infrastructure network.

The laboratory networks will be separated from this network.

---

# 8. Network Architecture

The target architecture is based on VLAN segmentation.

The Proxmox host will provide a VLAN trunk to the managed switching infrastructure using the 10GbE interface.

Proposed topology:

    Internet
       |
    Internet Gateway
       |
      UX7
       |
       | 
    Managed Switch
       |
       | 10GbE VLAN trunk
       |
     nic8
       |
    Proxmox
       |
       +-----------------------------+
       |                             |
    VM Networks                 Management
       |
       +---- Blue Team
       |
       +---- Red Team
       |
       +---- AI
       |
       +---- OT
       |
       +---- OT DMZ
       |
       +---- Detonation
       |
       +---- Lab Services

The exact switch model remains undecided.

Switch procurement is currently paused until the final architecture and port requirements have been established.

---

# 9. VLAN Design

The current proposed VLAN plan is:

| VLAN | Network | Purpose |
|---:|---|---|
| 10 | 192.168.10.0/24 | Infrastructure Management |
| 20 | 192.168.20.0/24 | Trusted Lab |
| 30 | 192.168.30.0/24 | AI |
| 40 | 192.168.40.0/24 | OT / ICS |
| 50 | 192.168.50.0/24 | Red Team |
| 60 | 192.168.60.0/24 | OT DMZ |
| 70 | 192.168.70.0/24 | Blue Team / SOC |
| 80 | 192.168.80.0/24 | Detonation |
| 90 | 192.168.90.0/24 | Lab Services |

Existing home network:

    192.168.0.0/24

The VLAN numbering is currently a design proposal and will be finalised before implementation.

---

# 10. Security Zones

The environment will be divided into logical security zones.

## Zone 1 - Home / Trusted Network

    192.168.0.0/24

Purpose:

- Normal household systems
- Existing infrastructure
- Internet access
- Administration

Laboratory systems should not have unrestricted access to this network.

---

## Zone 2 - Infrastructure Management

    VLAN 10
    192.168.10.0/24

Purpose:

- Proxmox management
- Network management
- Firewall management
- Infrastructure administration
- Management interfaces

Management access should be restricted to authorised administration systems.

---

## Zone 3 - Trusted Lab

    VLAN 20
    192.168.20.0/24

Purpose:

- Administrative systems
- General laboratory infrastructure
- Management workstations
- Non-security-sensitive laboratory services

---

## Zone 4 - AI

    VLAN 30
    192.168.30.0/24

Purpose:

- Local LLM infrastructure
- AI services
- AI agents
- Security AI workloads
- GPU workloads

AI workloads will not automatically have access to OT or Red Team networks.

---

## Zone 5 - OT / ICS

    VLAN 40
    192.168.40.0/24

Purpose:

- OT security training
- ICS simulation
- PLC simulation
- HMI
- Engineering workstation
- Industrial protocols
- OT monitoring

The OT network is treated as a separate security domain.

---

## Zone 6 - OT DMZ

    VLAN 60
    192.168.60.0/24

Purpose:

- Historian access
- Controlled services between IT and OT
- Security monitoring interfaces
- Jump hosts
- Controlled data exchange

The OT DMZ provides an intermediate security boundary between OT and other laboratory environments.

---

## Zone 7 - Red Team

    VLAN 50
    192.168.50.0/24

Purpose:

- Adversary simulation
- Security testing
- Attack simulation
- Vulnerable systems testing
- Controlled penetration testing

Potential systems:

- Kali Linux
- Windows test systems
- Linux test systems
- Vulnerable applications
- Security testing tools
- Adversary simulation tooling

The Red Team network will not have unrestricted access to the home network.

---

## Zone 8 - Blue Team / SOC

    VLAN 70
    192.168.70.0/24

Purpose:

- SIEM
- Log collection
- IDS
- Detection engineering
- Threat hunting
- Security monitoring
- Incident investigation

Expected telemetry sources include:

- Windows
- Linux
- Network devices
- Firewalls
- DNS
- Authentication systems
- OT systems
- Red Team systems

---

## Zone 9 - Detonation

    VLAN 80
    192.168.80.0/24

Purpose:

- Controlled malware-analysis exercises
- Suspicious file testing
- IOC generation
- Endpoint behaviour analysis
- Detection testing

This network should be isolated from the normal home network.

---

## Zone 10 - Lab Services

    VLAN 90
    192.168.90.0/24

Potential services:

- DNS
- DHCP
- NTP
- Internal repositories
- Supporting infrastructure
- Monitoring services
- Automation

---

# 11. Firewall Architecture

Inter-VLAN communication should be controlled by a dedicated firewall/router layer.

Initial security model:

    HOME
      |
      | Controlled
      v
    FIREWALL
      |
      +---- MANAGEMENT
      |
      +---- BLUE TEAM
      |
      +---- RED TEAM
      |
      +---- AI
      |
      +---- OT DMZ
      |
      +---- OT
      |
      +---- DETONATION
      |
      +---- LAB SERVICES

Default policy should be:

    DENY
    ↓
    Explicitly allow required traffic

Inter-zone communication should be documented before firewall rules are implemented.

---

# 12. OT Security Model

OT is intentionally isolated from the general-purpose laboratory.

Initial design:

    Corporate/Home
          |
          X
          |
       OT DMZ
          |
       Firewall
          |
          |
       OT Network
          |
     +----+----+
     |         |
    HMI       PLC
     |
 Engineering
 Workstation

Expected policy:

    HOME -> OT
    DENY

    OT -> HOME
    DENY

    OT -> INTERNET
    RESTRICTED

    RED TEAM -> OT
    CONTROLLED

    OT -> RED TEAM
    RESTRICTED

    BLUE TEAM -> OT
    CONTROLLED MONITORING

    AI -> OT
    EXPLICITLY CONTROLLED

The purpose is to replicate the security principles of segmented industrial environments rather than treating OT as another normal VLAN.

---

# 13. Blue Team Architecture

The Blue Team environment will provide the monitoring and detection layer.

Proposed architecture:

    Red Team
        |
        | Activity
        v
    Target Systems
        |
        | Logs / Telemetry
        v
    Log Collection
        |
        v
       SIEM
        |
        +---- Detection
        |
        +---- Correlation
        |
        +---- Threat Hunting
        |
        +---- IOC Analysis
        |
        v
    Blue Team Investigation

The environment should support repeatable detection engineering exercises.

---

# 14. Red Team / Adversary Simulation

The Red Team environment exists to generate controlled security telemetry.

Example workflow:

    Attack Simulation
          |
          v
    Target Endpoint
          |
          v
    Security Telemetry
          |
          v
        SIEM
          |
          v
    Detection Rule
          |
          v
    Investigation
          |
          v
       IOC Found
          |
          v
    Detection Improved

The objective is not simply to run attacks.

The objective is to understand:

1. What activity was generated
2. What telemetry was produced
3. What the SIEM received
4. Which detection identified it
5. Which indicators were available
6. Which indicators were missed
7. How the detection can be improved

---

# 15. AI Infrastructure

The AI environment will be hosted locally within the Proxmox infrastructure.

Potential workloads:

- Local LLM inference
- AI agents
- Security analysis
- Log analysis
- IOC analysis
- Threat intelligence assistance
- Security education
- Controlled automation
- Development workloads

AI workloads will be isolated using the AI VLAN.

---

# 16. Home AI

The project's general-purpose private AI environment is referred to internally as:

    Home AI

Home AI is intended for general local AI workloads, including:

- Local LLM inference
- Writing assistance
- Book development
- Research
- Creative workloads
- Private AI experimentation

Home AI is logically separated from the Red Team and OT networks.

The Home AI service should not require direct access to vulnerable laboratory systems.

---

# 17. GPU Expansion

The current planned GPU is:

    NVIDIA Tesla P40

Initial deployment:

    1 × Tesla P40

Future expansion may include:

    2 × Tesla P40

Before installation, the following will be validated:

- PCIe slot compatibility
- Riser compatibility
- Physical clearance
- Server power budget
- GPU power requirements
- Cooling requirements
- Proxmox PCIe passthrough
- IOMMU grouping
- Driver compatibility
- VM allocation strategy

The GPU is primarily intended for local AI workloads.

---

# 18. Proxmox VM Architecture

The final VM inventory will be divided by function.

## Infrastructure

    Firewall
    DNS
    DHCP
    NTP
    Management
    Monitoring

## Blue Team

    SIEM
    Log Collector
    IDS
    Threat Hunting
    Security Monitoring

## Red Team

    Kali Linux
    Windows Test
    Linux Test
    Vulnerable Applications
    Adversary Simulation

## OT

    Engineering Workstation
    HMI
    PLC Simulator
    Historian
    OT Services
    OT DMZ

## AI

    AI Infrastructure
    Security AI
    AI Agent
    GPU Workload VM

## Home AI

    Home AI
    LLM Services
    Writing Services

---

# 19. Resource Allocation Strategy

The server provides:

    32 logical CPUs
    256 GB RAM
    ~1.5 TB VM storage

Resources should not be statically allocated to every VM at maximum capacity.

The environment will use resource allocation based on workload.

Priority:

    1. Proxmox / Infrastructure
    2. Firewall / Network
    3. SIEM / Blue Team
    4. OT
    5. Red Team
    6. AI
    7. Home AI

Actual VM sizing will be documented separately.

---

# 20. Network Interface Strategy

Current:

    nic7
       |
       +---- vmbr0
              |
              +---- 192.168.0.100/24

Future:

    nic8
       |
       | 10GbE RJ45
       |
    Managed Switch
       |
       | 802.1Q VLAN trunk
       |
    Proxmox
       |
       +---- VLAN 10
       +---- VLAN 20
       +---- VLAN 30
       +---- VLAN 40
       +---- VLAN 50
       +---- VLAN 60
       +---- VLAN 70
       +---- VLAN 80
       +---- VLAN 90

`nic9` remains available for future use.

Potential future uses:

- Network redundancy
- Dedicated storage traffic
- Additional trunk
- Network monitoring
- Physical lab separation

---

# 21. Switch Requirements

Switch procurement is currently paused.

The eventual managed switch should support:

- IEEE 802.1Q VLANs
- VLAN trunking
- 1GbE RJ45
- Sufficient access ports for lab systems
- 10GbE connectivity suitable for the BCM57810
- Port isolation
- Port mirroring
- LACP
- Management interface

PoE is not required.

The final switch will be selected after the VM and network design has been finalised.

---

# 22. Management Model

Management access should follow a dedicated management-plane design.

Example:

    Admin Workstation
          |
          v
    Management VLAN
          |
       Firewall
          |
     +----+-----+
     |          |
   Proxmox      iLO
     |
     +---- Network Infrastructure
     |
     +---- Lab Services

Management interfaces should not be directly exposed to Red Team, Detonation or OT networks.

---

# 23. Logging Architecture

Security telemetry should be centralised.

Target architecture:

    Windows
       |
    Linux
       |
    Network
       |
      OT
       |
    Security Tools
       |
       v
   Log Collector
       |
       v
      SIEM
       |
       +---- Detection
       +---- Correlation
       +---- Investigation
       +---- Dashboards
       +---- IOC Analysis

The Red Team environment should intentionally generate telemetry that can be consumed by the Blue Team environment.

---

# 24. Backup Strategy

Backup requirements will be defined before production-like services are deployed.

Priority systems:

1. Proxmox configuration
2. Firewall configuration
3. SIEM configuration
4. Blue Team infrastructure
5. OT laboratory configurations
6. AI configuration
7. Home AI data
8. Test VM templates

Ephemeral Red Team and Detonation systems may be rebuilt from templates rather than backed up individually.

---

# 25. Security Boundaries

The following boundaries are considered mandatory design requirements:

    Internet
       |
       X
       |
    Vulnerable Lab

Laboratory systems must not be directly exposed to the public Internet unless explicitly required for a controlled exercise.

Similarly:

    Red Team
       X
    Home LAN

    OT
       X
    Home LAN

    Detonation
       X
    Home LAN

    OT
       X
    Internet

unless explicitly permitted by firewall policy.

---

# 26. Current Implementation Status

## Completed

- Proxmox VE installed
- Debian 13 host identified
- DL380p Gen8 hardware inventoried
- CPU inventory completed
- RAM inventory completed
- Storage inventory completed
- PCIe inventory completed
- Network interface inventory completed
- Fibre Channel adapter identified
- 1GbE interfaces identified
- 10GbE interfaces identified
- 10GbE interfaces confirmed as RJ45 copper
- Existing Proxmox interface identified
- Existing home network identified
- Initial VLAN architecture defined
- Security zones defined
- OT segmentation requirements defined
- AI environment defined
- Home AI environment defined
- Future GPU expansion identified

## Pending

- Managed switch selection
- Firewall selection
- VLAN implementation
- Proxmox network redesign
- VM inventory
- VM resource allocation
- SIEM deployment
- Blue Team deployment
- Red Team deployment
- OT lab deployment
- AI platform deployment
- GPU installation
- Backup architecture
- Monitoring architecture

---

# 27. Deployment Phases

## Phase 1 - Infrastructure

    Proxmox
      |
    Network
      |
    Firewall
      |
    VLANs
      |
    DNS / DHCP
      |
    Management

---

## Phase 2 - Blue Team

    Log Collection
          |
         SIEM
          |
        IDS
          |
    Detection Engineering
          |
     Threat Hunting

---

## Phase 3 - Red Team

    Kali
      |
    Test VMs
      |
    Attack Simulation
      |
    Telemetry Generation
      |
    Blue Team Detection

---

## Phase 4 - OT

    OT Network
       |
    OT DMZ
       |
    Engineering Workstation
       |
       +---- HMI
       |
       +---- PLC Simulator
       |
       +---- Historian

---

## Phase 5 - AI

    AI Infrastructure
          |
       Local LLM
          |
      AI Agents
          |
    Security Analysis
          |
       Home AI

---

## Phase 6 - GPU

    Tesla P40
        |
    PCIe Passthrough
        |
      AI VM
        |
    Local LLM / AI

---

# 28. Target Architecture

The completed environment is intended to provide the following logical architecture:

                    INTERNET
                       |
                  INTERNET GW
                       |
                      UX7
                       |
                MANAGED SWITCH
                       |
                    10GbE
                       |
                    PROXMOX
                       |
       +---------------+----------------+
       |               |                |
   MANAGEMENT        LAB VLANs       STORAGE
       |               |
       |       +-------+--------+
       |       |       |        |
       |      RED    BLUE      AI
       |       |       |        |
       |       |      SIEM      |
       |       |                |
       |       |             HOME AI
       |       |
       |       +---- Controlled
       |             testing
       |
       +---- iLO / Proxmox

                       |
                    OT DMZ
                       |
                    OT FIREWALL
                       |
                    OT NETWORK
                       |
             +---------+---------+
             |         |         |
            HMI      PLC       ENG WS

---

# 29. Design Objectives

The final platform should provide a repeatable laboratory capable of supporting:

- Cybersecurity monitoring
- SOC analyst training
- Threat hunting
- IOC investigation
- Detection engineering
- Adversary simulation
- SIEM engineering
- Windows security monitoring
- Linux security monitoring
- Network security monitoring
- OT / ICS security training
- AI experimentation
- Local LLM workloads
- GPU-accelerated AI workloads

The core operational model is:

    GENERATE
       |
    TELEMETRY
       |
    DETECT
       |
    INVESTIGATE
       |
    IDENTIFY IOC
       |
    RESPOND
       |
    IMPROVE DETECTION
       |
    REPEAT

---

# 30. Repository Structure

The repository should eventually be organised approximately as:

    homelab/
    |
    ├── README.md
    |
    ├── architecture/
    │   ├── network.md
    │   ├── vlan-plan.md
    │   ├── security-zones.md
    │   └── physical-infrastructure.md
    |
    ├── proxmox/
    │   ├── host-config.md
    │   ├── network-config.md
    │   └── vm-inventory.md
    |
    ├── firewall/
    │   ├── architecture.md
    │   └── rules.md
    |
    ├── blueteam/
    │   ├── siem.md
    │   ├── logging.md
    │   └── detection.md
    |
    ├── redteam/
    │   ├── architecture.md
    │   └── test-environment.md
    |
    ├── ot/
    │   ├── architecture.md
    │   ├── network.md
    │   └── systems.md
    |
    ├── ai/
    │   ├── architecture.md
    │   ├── security-ai.md
    │   └── gpu.md
    |
    ├── home-ai/
    │   ├── architecture.md
    │   └── services.md
    |
    └── documentation/
        ├── build-log.md
        └── troubleshooting.md

---

# 31. Change Control

Infrastructure changes should be documented before implementation where practical.

For significant changes record:

- Date
- Change
- Reason
- Affected systems
- Network impact
- Security impact
- Rollback procedure
- Result

Example:

    Date:
    Change:
    Reason:
    Systems:
    Network:
    Security impact:
    Rollback:
    Result:

---

# 32. Current State

The project is currently in the infrastructure design and validation phase.

The DL380p Gen8 has been inventoried and the core hardware capabilities are known.

The next engineering task is to convert the logical design into a concrete implementation plan consisting of:

1. Physical network topology
2. Managed switch requirements
3. Firewall architecture
4. VLAN implementation
5. Proxmox bridge configuration
6. VM inventory
7. CPU/RAM/storage allocation
8. Blue Team/SIEM architecture
9. Red Team architecture
10. OT architecture
11. AI architecture
12. GPU deployment plan

Hardware purchases should be made after these requirements have been finalised.

---

# 33. Engineering Principle

The environment will be built incrementally.

No individual component should dictate the architecture.

The architecture determines:

    Requirements
        |
        v
    Hardware
        |
        v
    Configuration
        |
        v
    Deployment
        |
        v
    Testing
        |
        v
    Documentation

The objective is to produce a maintainable, segmented and reproducible homelab rather than simply deploying a collection of virtual machines.
