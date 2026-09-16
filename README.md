# 🛡️ Cybersecurity

[🏠 Home](../../) | [🏗️ Architecture](../../tree/architecture) | [🌐 Networking](../../tree/networking) | [🔀 VLANs](../../tree/VLAN-%26-Network-Segmentation) | [⚙️ Proxmox](../../tree/proxmox) | [🖥️ Hardware](../../tree/hardware-inventory) | [🛠️ Configuration](../../tree/configuration)

[🗺️ Roadmap](../../tree/roadmap) | [🚀 Deployment](../../tree/deployment) | [🔐 Access Management](../../tree/access-management) | [🧪 Testing Lab](../../tree/testing-lab) | [🏭 OT/ICS](../../tree/ot-ics) | [📚 Documentation](../../tree/documentation) | [💾 Backup & DR](../../tree/backup-disaster-recovery)

[📊 Monitoring](../../tree/monitoring) | [🛡️ Cybersecurity](../../tree/cybersecurity) | [🤖 Home AI](../../tree/home-ai) | [🎮 GPU](../../tree/gpu) | [🖥️ Virtual Machines](../../tree/virtual-machines) | [💽 Storage](../../tree/storage) | [🏗️ Infrastructure](../../tree/infrastructure)

---

# 🎯 Purpose

This page documents the cybersecurity architecture for the homelab.

The environment is being designed as both:

1. A functional homelab infrastructure platform
2. A realistic cybersecurity training and testing environment

The security architecture will therefore support:

- Defensive security
- SOC operations
- SIEM engineering
- Detection engineering
- Threat hunting
- Endpoint monitoring
- Network security
- Vulnerability management
- Incident response
- Purple-team testing
- OT/ICS security
- MITRE ATT&CK
- Security automation

---

# 🧭 Security Architecture

The overall security model is based on layered controls.

```text
                         INTERNET
                            │
                            ▼
                     Router / Firewall
                            │
                            ▼
                    Network Segmentation
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                   │
        ▼                   ▼                   ▼
   Management             Users              Security
        │                   │                   │
        │                   │                   ▼
        │                   │                 Wazuh
        │                   │                   │
        ▼                   ▼                   ▼
     Proxmox              Systems          Security Events
        │
   ┌────┼───────────────┐
   │    │               │
   ▼    ▼               ▼
  VMs   Containers      GPU / AI
   │
   ├───────────────┐
   │               │
   ▼               ▼
Testing Lab       OT/ICS
