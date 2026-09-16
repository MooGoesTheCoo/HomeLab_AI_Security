# ⚙️ Proxmox

This section documents the Proxmox side of the homelab.

Proxmox is effectively the foundation that sits between the physical server and the virtual machines and containers running inside the lab.

The aim is to build it properly from the beginning, document the configuration and make the environment easy to rebuild if something goes wrong.

---

# 🖥️ The Proxmox Host

The Proxmox host is running on the HP ProLiant DL380p Gen8.

```text
┌────────────────────────────────────────────┐
│              HP DL380p Gen8                │
│                                            │
│                Proxmox VE                  │
│                                            │
├────────────────────────────────────────────┤
│                                            │
│  Virtual Machines                          │
│                                            │
│  Containers                                │
│                                            │
│  GPU Passthrough                           │
│                                            │
│  Virtual Networking                        │
│                                            │
│  Storage                                   │
│                                            │
└────────────────────────────────────────────┘
