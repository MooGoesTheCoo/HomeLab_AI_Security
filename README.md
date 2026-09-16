# 🤖 Home AI

This section documents the local AI environment being built inside the homelab.

The goal is to have a capable AI environment running locally on my own hardware rather than relying entirely on cloud-based AI services.

This is one of the main reasons for adding GPU capability to the server.

The environment will run on the Proxmox platform and make use of the NVIDIA Tesla P40.

---

# 🧠 What is Home AI?

Home AI is the name I'm using for the local AI environment in this homelab.

The idea is to create a place where I can experiment with:

- Local Large Language Models
- AI assistants
- Document processing
- Knowledge bases
- Embeddings
- Vector databases
- Automation
- AI agents
- Local applications
- GPU-accelerated workloads

The environment will be designed so that different AI services can be added or removed without rebuilding the entire platform.

---

# 🏗️ High-Level Architecture

The basic architecture will look like this:

```text
                         INTERNET
                            │
                            ▼
                         UX7
                            │
                            ▼
                     Managed Switch
                            │
                            ▼
                        Proxmox
                            │
                            ▼
                       Home AI VM
                            │
              ┌─────────────┼─────────────┐
              │             │             │
              ▼             ▼             ▼
           AI Engine     Web UI       Databases
              │
              ▼
          CUDA Runtime
              │
              ▼
          Tesla P40
