# 💾 Backup & Disaster Recovery

This section documents how the homelab will protect itself against things going wrong.

Because this is a lab, things are going to break.

That's part of the point.

The important thing is being able to recover without having to rebuild everything from scratch.

The backup strategy will therefore be designed around a simple principle:

> **Experiment freely, but make sure important things can be recovered.**

---

# 🎯 What Are We Protecting?

The homelab contains several different types of data.

```text
                         HOMELAB
                            │
          ┌─────────────────┼─────────────────┐
          │                 │                 │
          ▼                 ▼                 ▼
       Proxmox              VMs             Data
          │                 │                 │
          │          ┌──────┼──────┐          │
          │          │      │      │          │
          ▼          ▼      ▼      ▼          ▼
       Config      Wazuh   AI   Windows   Documents
