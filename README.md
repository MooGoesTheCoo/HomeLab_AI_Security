# 🔐 Access Management

This section documents how access to the homelab is controlled.

The homelab contains several systems that should not be freely accessible to every device or user.

The basic idea is:

> **Only give access where it is needed, and don't make management interfaces unnecessarily accessible.**

This includes physical management such as iLO, virtualisation management through Proxmox, operating systems, network equipment and applications.

---

# 🎯 What Are We Protecting?

The access-management design covers:

- Proxmox
- iLO
- Ubiquiti UX7
- Managed switch
- Virtual machines
- Linux systems
- Windows systems
- Wazuh
- Home AI
- OT/ICS systems
- Backup infrastructure

---

# 🏗️ Access Architecture

A simplified model is:

```text
                         HOME NETWORK
                              │
                              │
                         Firewall / UX7
                              │
                              ▼
                       Management VLAN
                              │
             ┌────────────────┼────────────────┐
             │                │                │
             ▼                ▼                ▼
          Proxmox            iLO            Switch
             │
             │
      ┌──────┼────────┐
      │      │        │
      ▼      ▼        ▼
    Wazuh  Home AI   Test VMs
