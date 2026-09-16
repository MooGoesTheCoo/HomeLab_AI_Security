# 🖥️ Virtual Machines & Containers

This section documents the virtual machines and containers that will run inside the homelab.

The idea behind the lab is to use the physical server as a shared platform rather than having a separate physical machine for every job.

Proxmox gives me the ability to create different environments, give them the resources they need and keep them separated from each other.

---

# 🏠 The Idea

The physical server is the foundation.

Proxmox sits on top of the hardware.

Everything else runs inside it.


                    HP DL380p Gen8
                           │
                           ▼
                      Proxmox VE
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
      Home AI           Wazuh          Security Lab
         VM                VM               VMs
          │                │                │
          ▼                ▼                ▼
       Tesla P40       Security          Windows
       GPU Workload    Monitoring          Linux
                                         Testing
