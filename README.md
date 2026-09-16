# 🏗️ Homelab Architecture

This page provides the high-level architecture for the entire homelab.

The purpose of this page is to show how the different parts of the project fit together.

It is the **map of the homelab**.

Detailed hardware, Proxmox, networking, VLANs, Wazuh, Home AI and OT/ICS configuration are documented on their individual pages.

---

# 🎯 Project Overview

The homelab is being built as a self-contained environment for:

- Cybersecurity learning
- SOC development
- Blue Team activities
- Red Team testing
- OT/ICS security
- Security monitoring
- SIEM and log analysis
- Local AI workloads
- Virtualisation
- Network security experimentation
- Infrastructure and automation testing

The design is intended to allow different environments to operate independently while still allowing controlled communication between them.

---

# 🧱 Core Architecture

The overall architecture is built around four major layers:

```text
┌─────────────────────────────────────────────────────────┐
│                    PHYSICAL LAYER                       │
│                                                         │
│  HP DL380p Gen8                                        │
│  Ubiquiti UX7                                          │
│  Managed Switch                                        │
│  Standalone PCs                                        │
│  iLO                                                    │
└───────────────────────────┬─────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────┐
│                  VIRTUALISATION LAYER                   │
│                                                         │
│  Proxmox VE                                             │
│  Virtual Machines                                      │
│  Containers                                             │
│  Virtual Networking                                    │
│  GPU Passthrough                                       │
└───────────────────────────┬─────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────┐
│                     NETWORK LAYER                       │
│                                                         │
│  VLANs                                                  │
│  Trunking                                               │
│  Firewall / Routing                                     │
│  Network Segmentation                                   │
│  Management Networks                                    │
└───────────────────────────┬─────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────┐
│                  WORKLOAD / SECURITY LAYER              │
│                                                         │
│  Wazuh                                                  │
│  Blue Team                                              │
│  Red Team                                               │
│  OT / ICS                                               │
│  Home AI                                                │
│  Security Testing                                      │
└─────────────────────────────────────────────────────────┘
