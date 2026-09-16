# 🗺️ Homelab Roadmap

This is the overall roadmap for building the homelab.

The project is deliberately being built in stages.

There is no point trying to build everything at once.

The idea is to get the foundations working properly, prove they work, and then build the next layer on top.

---

# 🎯 End Goal

The finished homelab should provide:

- A reliable virtualisation platform
- Segmented networking
- Centralised security monitoring
- A dedicated cybersecurity testing environment
- A local Home AI environment
- GPU acceleration
- An OT/ICS security environment
- Infrastructure monitoring
- Backup and recovery
- Secure administration
- Documented security testing
- A repeatable build process

The end result should be something that is useful for both **learning and practical experimentation**.

---

# 🏗️ The Build

The overall project can be thought of as these layers:

```text
                    ┌───────────────────┐
                    │    Applications   │
                    │ Home AI / Wazuh   │
                    │ OT / Testing      │
                    └─────────┬─────────┘
                              │
                    ┌─────────▼─────────┐
                    │   Virtual Machines │
                    └─────────┬─────────┘
                              │
                    ┌─────────▼─────────┐
                    │     Proxmox        │
                    └─────────┬─────────┘
                              │
                    ┌─────────▼─────────┐
                    │ Storage / Hardware │
                    └─────────┬─────────┘
                              │
                    ┌─────────▼─────────┐
                    │      Network       │
                    └───────────────────┘
