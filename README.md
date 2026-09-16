# 🖥️ Infrastructure

This section documents the physical hardware that everything else in the homelab is built around.

The idea is to start with the physical layer and work upwards.

Before worrying about VMs, AI, cybersecurity or networking, I want to understand exactly what hardware I have, what it's capable of and how everything is connected.

---

## 🏠 The Server

The main server is an **HP ProLiant DL380p Gen8**.

This is the machine that provides the main compute platform for the homelab.

Rather than using a modern desktop PC, I decided to make use of enterprise hardware and see how far I can push it.

The server provides:

- Enterprise-grade hardware
- Multiple CPU cores
- Large memory capacity
- Multiple PCIe expansion slots
- Dedicated remote management through iLO
- Multiple network interfaces
- Redundant power capability
- Plenty of room for storage expansion
- GPU expansion capability

The server will ultimately run **Proxmox VE**, which becomes the foundation for the virtualised side of the lab.

---

# 🧱 Physical Architecture

At a high level, the physical environment looks like this:

```text
                         INTERNET
                            │
                            ▼
                    ┌───────────────┐
                    │  Ubiquiti UX7 │
                    │    Router     │
                    └───────┬───────┘
                            │
                            ▼
                    ┌───────────────┐
                    │ Managed Switch│
                    └───────┬───────┘
                            │
                 ┌──────────┴──────────┐
                 │                     │
                 ▼                     ▼
          Homelab Server         Standalone PCs
          DL380p Gen8
                 │
        ┌────────┴────────┐
        │                 │
        ▼                 ▼
     Proxmox             iLO
        │            Management
        │
   ┌────┴─────────────────────────┐
   │                              │
   ▼                              ▼
 Virtual Machines             Home AI
 Containers                       │
                                  ▼
                             Tesla P40
