# 🏗️ Architecture

This section documents how the different parts of the homelab fit together.

The other branches describe individual parts of the project.

This branch brings them together.

The objective is to have a clear picture of:

- The physical hardware
- The network
- Proxmox
- Storage
- Virtual machines
- GPU
- Home AI
- Wazuh
- Monitoring
- Backup
- OT/ICS
- Security testing

---

# 🎯 The Big Picture

The homelab is being built as a small private infrastructure and cybersecurity environment.

At a high level:

```text
                         INTERNET
                            │
                            ▼
                         UX7
                            │
                            ▼
                     MANAGED SWITCH
                            │
                            ▼
                       DL380p Gen8
                            │
                         Proxmox
                            │
          ┌─────────────────┼─────────────────┐
          │                 │                 │
          ▼                 ▼                 ▼
       Security          Home AI          Test Lab
        / Wazuh             │                 │
                            ▼                 │
                         Tesla P40            │
                                              │
                              ┌───────────────┘
                              │
                              ▼
                           OT / ICS
