# 🚀 Deployment

This section documents the actual deployment order for the homelab.

The project contains quite a few different systems, and they can't all be installed at the same time.

Some systems depend on others being available first.

For example:

```text
Network
   │
   ▼
Proxmox
   │
   ▼
Storage
   │
   ▼
Virtual Machines
   │
   ├── Wazuh
   ├── Home AI
   └── Testing Lab
