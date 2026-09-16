# 🛡️ Cybersecurity

This section documents the cybersecurity environment within the homelab.

The purpose of this part of the project is to create a realistic environment where security monitoring, detection engineering, incident investigation and security testing can be carried out safely.

The lab will use **Wazuh** as the permanent SIEM/security monitoring platform.

The intention is not simply to install security tools.

I want to build an environment where I can generate realistic security events, collect the telemetry, investigate what happened and then improve the detections.

---

# 🎯 What is the Security Lab?

The cybersecurity environment will provide a controlled place to experiment with security.

It will eventually contain:

- Windows systems
- Linux systems
- Wazuh
- Security monitoring
- Endpoint telemetry
- Network telemetry
- Attack simulation
- Detection engineering
- Purple-team testing
- Incident investigation

The environment should be isolated from the normal home network.

---

# 🏗️ High-Level Architecture

The basic concept is:

```text
                         Proxmox
                            │
              ┌─────────────┼─────────────┐
              │             │             │
              ▼             ▼             ▼
          Windows VM     Linux VM       Wazuh
              │             │             │
              │             │             │
              └─────────────┼─────────────┘
                            │
                            ▼
                     Security Telemetry
                            │
                            ▼
                         Wazuh
                            │
                            ▼
                    Alerts / Analysis
