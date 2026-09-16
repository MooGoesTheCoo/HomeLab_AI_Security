# 🖥️ Hardware Inventory

This section documents the physical hardware used by the homelab.

The goal is simple:

> Know exactly what hardware is available before deciding what we are going to run on it.

Rather than guessing specifications, the actual server configuration will be recorded here as it is discovered.

---

# 🖥️ Primary Server

| Item | Details | Status |
|---|---|---|
| Manufacturer | HP | 🟢 |
| Model | DL380p Gen8 | 🟢 |
| Form Factor | Rack Server | 🟢 |
| CPU | 2 × Intel Xeon E5-2650 v2 | 🟢 |
| CPU Count | 2 | 🟢 |
| RAM | 256 GB | 🟢 |
| Storage | ~1.6 TB logical volume | 🟢 |
| RAID Controller | HP Smart Array P420i | 🟢 |
| Network | TBD | 🟡 |
| GPU | Tesla P40 24 GB | 🟡 |
| iLO | iLO | 🟢 |

---

# 🧠 CPU

The server contains two Intel Xeon E5-2650 v2 processors.

| CPU | Model | Cores | Threads | Frequency | Status |
|---|---|---:|---:|---:|---|
| CPU 1 | Intel Xeon E5-2650 v2 | 8 | 16 | 2.60 GHz / 3.40 GHz Turbo | 🟢 |
| CPU 2 | Intel Xeon E5-2650 v2 | 8 | 16 | 2.60 GHz / 3.40 GHz Turbo | 🟢 |

### CPU Summary

| Specification | Value |
|---|---|
| Physical CPUs | 2 |
| Physical Cores | 16 |
| Logical CPUs / Threads | 32 |
| Threads per Core | 2 |
| Base Frequency | 2.60 GHz |
| Maximum Frequency | 3.40 GHz |
| Architecture | x86_64 |
| Virtualisation | Intel VT-x |
| NUMA Nodes | 2 |

### NUMA Layout

```text
NUMA Node 0
├── CPU 1
├── CPUs 0-7
└── CPUs 16-23

NUMA Node 1
├── CPU 2
├── CPUs 8-15
└── CPUs 24-31

---

# 🧠 RAM

The DL380p memory configuration will be recorded here.

| Slot | Size | Type | Speed | Status |
|---|---:|---|---:|---|
| DIMM 1 | TBD | TBD | TBD | 🟡 |
| DIMM 2 | TBD | TBD | TBD | 🟡 |
| DIMM 3 | TBD | TBD | TBD | 🟡 |
| DIMM 4 | TBD | TBD | TBD | 🟡 |
| DIMM 5 | TBD | TBD | TBD | 🟡 |
| DIMM 6 | TBD | TBD | TBD | 🟡 |

Additional DIMMs will be added when identified.

### RAM Checks

- [ ] Total RAM confirmed
- [ ] DIMM layout confirmed
- [ ] Memory type confirmed
- [ ] Memory speed confirmed
- [ ] Population rules checked
- [ ] Upgrade capacity identified

---

# 💾 Storage

All physical storage will be recorded here.

| Drive | Model | Capacity | Interface | Bay | Status |
|---|---|---:|---|---:|---|
| Drive 1 | TBD | TBD | TBD | TBD | 🟡 |
| Drive 2 | TBD | TBD | TBD | TBD | 🟡 |
| Drive 3 | TBD | TBD | TBD | TBD | 🟡 |
| Drive 4 | TBD | TBD | TBD | TBD | 🟡 |
| Drive 5 | TBD | TBD | TBD | TBD | 🟡 |
| Drive 6 | TBD | TBD | TBD | TBD | 🟡 |
| Drive 7 | TBD | TBD | TBD | TBD | 🟡 |
| Drive 8 | TBD | TBD | TBD | TBD | 🟡 |

More drive bays can be added if required.

---

# 🗄️ RAID Controller

| Item | Value |
|---|---|
| Controller | TBD |
| Firmware | TBD |
| Cache | TBD |
| Battery / Flash Backup | TBD |
| RAID Level | TBD |
| Logical Drives | TBD |
| Status | 🟡 |

### RAID Checks

- [ ] Controller identified
- [ ] Firmware checked
- [ ] Cache identified
- [ ] Battery/FBWC status checked
- [ ] Physical drives identified
- [ ] Logical drives identified
- [ ] RAID configuration documented

---

# 🎮 GPU

The server is intended to support local AI workloads.

Current GPU:

| GPU | Model | VRAM | PCIe | Purpose | Status |
|---|---|---:|---|---|---|
| GPU 1 | Tesla P40 | 24 GB | TBD | Home AI | 🟡 |
| GPU 2 | TBD | TBD | TBD | Future expansion | 🔴 |

A second P40 may be added later.

The final GPU configuration will depend on:

- PCIe slot availability
- Power requirements
- Cooling
- GPU passthrough
- Proxmox compatibility
- AI workload requirements

---

# 🔌 PCIe Slots

The PCIe slot layout will be documented using the actual server configuration.

| Slot | Type | Width | Current Usage | Device |
|---|---|---|---|---|
| PCI-E Slot 1 | PCIe Gen 3 | x16 | In Use | TBD |
| PCI-E Slot 2 | TBD | TBD | TBD | TBD |
| PCI-E Slot 3 | TBD | TBD | TBD | TBD |
| PCI-E Slot 4 | TBD | TBD | TBD | TBD |
| PCI-E Slot 5 | TBD | TBD | TBD | TBD |
| PCI-E Slot 6 | TBD | TBD | TBD | TBD |

The exact slot configuration will be verified before installing additional GPUs.

---

# 🌐 Network Interfaces

| Interface | Model | Speed | MAC | Purpose | Status |
|---|---|---:|---|---|---|
| NIC 1 | TBD | TBD | TBD | Management | 🟡 |
| NIC 2 | TBD | TBD | TBD | VM Traffic | 🟡 |
| NIC 3 | TBD | TBD | TBD | TBD | 🟡 |
| NIC 4 | TBD | TBD | TBD | TBD | 🟡 |

Additional interfaces will be documented if present.

---

# 🔧 Network Adapter / HBA Cards

Additional PCIe cards will be documented here.

| Device | Model | Slot | Purpose | Status |
|---|---|---|---|---|
| NIC | TBD | TBD | Network | 🟡 |
| HBA | TBD | TBD | Storage | 🟡 |
| Other | TBD | TBD | TBD | 🟡 |

---

# 🖥️ iLO

iLO provides out-of-band management for the server.

| Item | Value |
|---|---|
| iLO Version | TBD |
| Firmware | TBD |
| IP Address | TBD |
| MAC Address | TBD |
| Dedicated Port | TBD |
| Shared Port | TBD |
| Status | 🟡 |

### iLO Checks

- [ ] iLO accessible
- [ ] Firmware identified
- [ ] Network configured
- [ ] Administrator access secured
- [ ] Remote console tested
- [ ] Hardware monitoring verified

---

# ⚡ Power

| Item | Value |
|---|---|
| PSU 1 | TBD |
| PSU 2 | TBD |
| PSU Wattage | TBD |
| Redundant Power | TBD |
| Power Connections | TBD |

GPU installation will require checking available power capacity.

---

# 🌡️ Cooling

The server will be checked for adequate cooling before GPU workloads are introduced.

Items to verify:

- [ ] Fan configuration
- [ ] Fan health
- [ ] CPU temperatures
- [ ] GPU temperatures
- [ ] Airflow
- [ ] GPU cooling
- [ ] Rack position

---

# 🧩 Server Expansion

Potential future upgrades include:

- Additional RAM
- Additional storage
- Second Tesla P40
- Additional network interfaces
- Additional storage controllers
- Other PCIe devices

Any hardware changes should be recorded in this document.

---

# 📋 Hardware Summary

| Category | Current Status |
|---|---|
| Server | 🟢 DL380p Gen8 |
| CPU | 🟡 TBD |
| RAM | 🟡 TBD |
| Storage | 🟡 TBD |
| RAID | 🟡 TBD |
| GPU | 🟡 Tesla P40 |
| PCIe | 🟡 Being verified |
| Network | 🟡 TBD |
| iLO | 🟡 Being verified |
| Power | 🟡 TBD |
| Cooling | 🟡 TBD |

---

# 🔍 Hardware Discovery

Before finalising the virtualisation design, the following information should be collected from the server.

### Proxmox

```text
lscpu
free -h
lsblk
lspci
lsusb
ip -br link
