# 📊 Monitoring

This section documents how the homelab will be monitored.

The idea is simple:

> If something breaks, I want to know about it before I have to go looking for it.

The monitoring environment will cover the physical server, Proxmox, virtual machines, storage, networking, GPU and important services.

Security monitoring through Wazuh is documented separately in the cybersecurity section.

---

# 🎯 What Are We Monitoring?

The homelab contains quite a few different layers.

```text
                    Homelab
                       │
       ┌───────────────┼────────────────┐
       │               │                │
       ▼               ▼                ▼
    Hardware         Proxmox         Network
       │               │                │
       ▼               ▼                ▼
     Server            VMs             UX7
     Disks          Containers        Switch
     CPU               │
     RAM               ▼
     GPU             Services
