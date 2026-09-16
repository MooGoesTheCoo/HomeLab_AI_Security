# 🌐 Networking

This section documents the network that connects the homelab together.

The aim is to build the network properly from the start rather than simply plugging everything into the same network and hoping for the best.

The network needs to support the normal home environment as well as the Proxmox server, iLO management, Home AI and the cybersecurity lab.

---

# 🏠 Network Overview

The basic physical layout is:

```text
                         INTERNET
                            │
                            ▼
                    ┌───────────────┐
                    │  Ubiquiti UX7 │
                    │    Router     │
                    └───────┬───────┘
                            │
                            │
                            ▼
                    ┌───────────────┐
                    │ Managed Switch│
                    └───────┬───────┘
                            │
              ┌─────────────┼─────────────┐
              │             │             │
              ▼             ▼             ▼
        DL380p Server    Standalone PC   Standalone PC
              │
       ┌──────┴──────┐
       │             │
       ▼             ▼
    Proxmox          iLO
       │
       │
 ┌─────┴─────────────────────────────┐
 │                                   │
 ▼                                   ▼
VMs / Containers                  Home AI
                                       │
                                       ▼
                                  Tesla P40
