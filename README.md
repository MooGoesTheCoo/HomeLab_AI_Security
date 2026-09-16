# 🎮 GPU

This section documents the GPU side of the homelab.

The main reason for adding a GPU is to give the Home AI environment enough processing power to run local AI workloads.

The current plan is to use an **NVIDIA Tesla P40** in the HP ProLiant DL380p Gen8.

This is one of the more interesting parts of the build because getting an older enterprise server to work with modern GPU workloads involves quite a few things to consider.

---

# 🎯 What is the GPU for?

The primary purpose of the GPU is **local AI**.

Instead of relying entirely on cloud-based AI services, I want to experiment with running models locally inside the homelab.

The GPU will provide acceleration for workloads that benefit from dedicated GPU processing.

The initial use case is:

```text
                    Proxmox
                       │
                       ▼
                  Home AI VM
                       │
                       ▼
                  Tesla P40
                       │
                       ▼
                 Local AI Models
