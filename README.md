# 🖥️ Proxmox Network

The primary server is an HP ProLiant DL380p Gen8 running Proxmox VE.

The current Proxmox network configuration has been verified directly from the host.

## Current Configuration

| Item | Value | Status |
|---|---|---|
| Hostname | `pve` | 🟢 Confirmed |
| Physical NIC | `nic7` | 🟢 Confirmed |
| NIC State | UP | 🟢 Confirmed |
| Proxmox Bridge | `vmbr0` | 🟢 Confirmed |
| Bridge State | UP | 🟢 Confirmed |
| Management IP | `192.168.0.100/24` | 🟢 Confirmed |
| Default Gateway | `192.168.0.1` | 🟢 Confirmed |
| Bridge Port | `nic7` | 🟢 Confirmed |
| STP | Off | 🟢 Confirmed |
| Bridge Forward Delay | `0` | 🟢 Confirmed |
| VLAN Aware | Not currently enabled | 🟡 Planned |
| VLAN Trunk | Not currently configured | 🟡 Planned |

## Current Network

```text
                    Ubiquiti UX7
                         │
                         │
                       nic7
                         │
                         ▼
                       vmbr0
                         │
                 192.168.0.100/24
                         │
                         ▼
                    Proxmox Host
