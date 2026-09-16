# 🏗️ Homelab Architecture

This page provides the high-level design of the homelab and shows how the physical hardware, Proxmox, networking, security environments, OT/ICS and Home AI fit together.

The goal is to build a flexible, segmented and security-focused environment that can be expanded over time.

---

# 🎯 Project Purpose

The homelab is being built for:

- Cybersecurity and SOC development
- Blue Team and Red Team testing
- OT/ICS security
- Wazuh security monitoring
- Local AI workloads
- Virtualisation
- Network security testing
- Detection engineering
- Security experimentation and learning

---

# 🧱 High-Level Architecture

```text
                         INTERNET
                            │
                            ▼
                       UBIQUITI UX7
                            │
                            ▼
                     MANAGED SWITCH
                            │
                       VLAN TRUNK
                            │
                            ▼
                    HP DL380p Gen8
                       PROXMOX VE
                            │
                          vmbr0
                            │
       ┌────────┬──────────┼──────────┬────────┬────────┐
       │        │          │          │        │
       ▼        ▼          ▼          ▼        ▼
    VLAN 10  VLAN 20    VLAN 30    VLAN 40  VLAN 50
    MGMT     BLUE       HOME AI    OT/ICS   RED TEAM
       │        │          │          │        │
      iLO      WAZUH      P40        OT      TESTING
                                      │
                                      ▼
                                   VLAN 60
                                   OT DMZ
