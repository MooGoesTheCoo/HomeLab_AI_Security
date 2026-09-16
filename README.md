# 💾 Storage

This section documents the storage used by the homelab.

Storage is something I want to get right early in the build because pretty much everything else depends on it.

Proxmox needs somewhere to store virtual machines and containers, the cybersecurity lab will generate data, and the Home AI environment will eventually need somewhere to keep models and other files.

The aim is to keep the storage simple, reliable and easy to recover.

---

# 🧱 Storage Architecture

At a high level, storage will look something like this:

```text
                    DL380p Gen8
                         │
                         ▼
                    Proxmox VE
                         │
              ┌──────────┼──────────┐
              │          │          │
              ▼          ▼          ▼
             VM        ISO       Backup
           Storage    Storage    Storage
              │
       ┌──────┴──────────┐
       │                 │
       ▼                 ▼
 Cybersecurity        Home AI
      VMs               VM
                          │
                          ▼
                       Models
