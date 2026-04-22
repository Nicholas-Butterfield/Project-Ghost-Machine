<h1 align="center">🜁 Project Ghost Machine</h1>
<h3 align="center">Fedora 43 Hardening • Sway TWM • 64GB Upgrade • Ghost Identity Node</h3>

<p align="center">
  Transforming a Dell Latitude 5430 into a hardened Linux-based privacy and cybersecurity workstation.
</p>

---

## Quick Overview

Project Ghost Machine is a full-system transformation of a Dell Latitude 5430 into a hardened, Linux‑based ghost identity node. This project documents the complete migration from Windows 11 Enterprise to Fedora 43, the implementation of the Sway tiling window manager, and the upcoming 64GB RAM hardware upgrade.

The goal is to create a secure, minimal‑surface‑area workstation optimized for privacy, cybersecurity workflows, and integration into a multi‑architecture home lab. Each phase of the project includes evidence, benchmarks, configuration details, and hardening steps to provide a transparent, real‑world case study in system security engineering.

---

## Table of Contents
- [Phase 1: Software Migration](#phase-1-software-migration-16gb-baseline)
- [Phase 2: Hardware Upgrade](#phase-2-hardware-upgrade)
- [Phase 3: Hardening](#phase-3-hardening)
- [Phase 4: Sway Optimization](#phase-4-sway-optimization)
- [Benchmarks](#benchmarks)
- [Threat Model](#threat-model)
- [Future Enhancements](#future-enhancements)

---

## Phase Roadmap

This project is structured into multiple phases to document the full transformation of the Dell Latitude 5430 into a hardened Linux-based ghost identity node. Each phase includes evidence, configuration details, and security considerations.

### **Phase 1 — Software Migration (Completed)**
- Migrated from Windows 11 Enterprise to Fedora 43
- Implemented Sway TWM for minimal attack surface
- Captured baseline RAM usage and system information
- Established initial system footprint for comparison

### **Phase 2 — Hardware Upgrade (In Progress)**
- Upgrade from 16GB to 64GB DDR4 RAM
- Document installation, BIOS validation, and stability testing
- Update benchmarks and system performance metrics

### **Phase 3 — System Hardening (Planned)**
- SELinux enforcing configuration
- Firewalld rules and service pruning
- SSH hardening and key-based authentication
- Auditd rules and system integrity monitoring
- Minimal package footprint and telemetry reduction

### **Phase 4 — Sway TWM Optimization (Planned)**
- Custom keybindings and workflow enhancements
- Secure lockscreen and idle behavior
- Wayland security benefits and configuration
- Performance tuning for low-resource overhead

### **Phase 5 — Benchmarks & Analysis (Planned)**
- RAM usage comparison (Windows vs. Fedora vs. 64GB upgrade)
- Boot time, CPU load, and power efficiency metrics
- Security posture comparison before/after hardening

### **Phase 6 — Threat Model & Future Enhancements (Planned)**
- Define threat actors and attack surfaces
- Map mitigations implemented across phases
- Identify remaining risks and future improvements

---

### 📸 Phase 1: Software Migration (16GB Baseline)

| Windows 11 Enterprise (Original) | Fedora Linux (Current State) |
| :------------------------------: | :--------------------------: |
| !["Windows baseline"](baseline_ram_usage.png) | !["Fedora 16GB info"](docs/fedora_system_info.png) |
| *Figure 1: Original Windows 11 Pro* | *Figure 2: Current Fedora Linux Install* |

> [!NOTE]
> Physical memory currently remains at the **16GB factory baseline**. Documentation for the **64GB RAM upgrade** will be added following hardware installation.
