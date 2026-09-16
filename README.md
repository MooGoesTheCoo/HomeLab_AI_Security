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



## And update your current-status table

Change the relevant entries to:

| Component | Current Status |
|---|---|
| Proxmox DL380p Gen8 | 🟢 Online |
| Proxmox `vmbr0` | 🟢 Confirmed |
| Proxmox Management IP | 🟢 `192.168.0.100/24` |
| Default Gateway | 🟢 `192.168.0.1` |
| Active NIC | 🟢 `nic7` |
| Physical NICs | 🟢 10 detected |
| VLAN-aware `vmbr0` | 🔴 Not configured |
| VLAN Trunk | 🔴 Not configured |
| Inter-VLAN Routing | 🔴 Not configured |
| Firewall Rules | 🔴 Not configured |
| OT Isolation | 🔴 Not configured |
| Wazuh Integration | 🔴 Not configured |

### One thing we need to establish before touching Proxmox

We need the **exact managed switch model** and its current configuration.

You previously mentioned the **Ubiquiti USW-Lite-8-PoE**, but we shouldn't assume that's the switch you're actually going to use.

Once we confirm the switch, I'll map:

**UX7 → switch → `nic7` → `vmbr0` → VLANs → VMs**

and then we can configure the trunk safely.
