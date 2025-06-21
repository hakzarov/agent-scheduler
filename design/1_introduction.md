# Introduction to Agent Scheduler

## Overview
The Agent Scheduler is a core module for scheduling compute tasks in a distributed agent network implemented initially on TON. It provides a flexible framework for managing virtualized workloads with security and efficiency as primary concerns.

## Key Principles
1. **Virtualization-Based Security**: Uses virtual machines (VMs) instead of containers for enhanced security isolation
2. **Flexible State Storage**: VM state can be stored:
   - Locally on compute nodes
   - In distributed storage systems
   - Chunked across multiple devices for light clients
   This enables efficient resource usage where devices (like those of train passengers) can contribute smol amounts of compute without excessive network traffic.
3. **Protocol Efficiency**: Google FlatBuffers for high-performance communication
4. **Extensible Architecture**: Proxmox as initial MVP with pluggable system integration
5. **Agent Specialization**: Support for diverse agent types with different resource requirements

## Why Virtual Machines?
While Docker/LXC containers are lightweight, they have demonstrated security vulnerabilities in multi-tenant environments. VMs provide:
- Stronger isolation guarantees
- Hardware-enforced security boundaries
- Mature snapshot/rollback capabilities
- Broader compatibility with legacy systems

The relatively smol overhead (<1% CPU overhead, 100MB-4GB of RAM and a few to a few hundreds of GB of storage per VM) is an acceptable tradeoff for enhanced security in sensitive workloads.
