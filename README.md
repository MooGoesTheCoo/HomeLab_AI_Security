# 🏭 OT / ICS Security

This section documents the Operational Technology (OT) and Industrial Control Systems (ICS) environment planned for the homelab.

The goal is to create a safe environment where I can learn how industrial systems work and, more importantly, how they can be monitored and protected.

This environment will eventually connect the technical knowledge from the cybersecurity lab with OT/ICS-specific security concepts.

---

# 🎯 Why OT / ICS?

Traditional IT environments and industrial environments have different priorities.

In a normal IT environment, confidentiality and availability are often major concerns.

In an industrial environment, safety and continuous operation can be critical.

A security test that is acceptable against a disposable Windows VM may not be acceptable against a real industrial control system.

That's why this lab will provide a controlled environment for learning and experimentation.

---

# 🏭 What is OT?

Operational Technology refers to systems used to monitor and control physical processes.

Examples include:

- Industrial control systems
- PLCs
- RTUs
- HMIs
- SCADA systems
- Industrial networks
- Sensors
- Actuators
- Engineering workstations

A simplified industrial environment might look like:

```text
                 Enterprise IT
                       │
                       │
                IT / OT Boundary
                       │
                       ▼
                  OT Network
                       │
          ┌────────────┼────────────┐
          │            │            │
          ▼            ▼            ▼
        SCADA         HMI          PLC
                                     │
                              Physical Process
