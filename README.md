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

* Migrated from Windows 11 Enterprise to Fedora 43
* Implemented Sway TWM for minimal attack surface
* Captured baseline RAM usage and system information

| Windows 11 Enterprise (Original) | Fedora Linux (Current State) |
| :---: | :---: |
| ![Windows 11](baseline_ram_usage.png) | ![Fedora 43](docs/fedora_system_info.png) |
| *Figure 1: Windows 16GB Baseline* | *Figure 2: Fedora 16GB Baseline* |

---

</details>
> [!NOTE]
> Physical memory currently remains at the **16GB factory baseline**. Documentation for the **64GB RAM upgrade** will be added following hardware installation.

---

### **Phase 2 — Hardware Upgrade (In Progress)**
- Upgrade from 16GB to 64GB DDR4 RAM
- Document installation, BIOS validation, and stability testing
- Update benchmarks and system performance metrics

## Benchmarks

This section captures performance metrics across the system’s lifecycle:  
1) Windows 11 Enterprise (factory state, 16GB RAM)  
2) Fedora 43 (post‑migration, 16GB RAM)  
3) Fedora 43 (post‑upgrade, 64GB RAM — pending hardware arrival)  
4) Fedora 43 (post‑hardening — planned)

The goal is to provide transparent, evidence‑based comparisons that show how the system evolves across each phase.

---

### **Baseline Memory Metrics (Windows 11 Enterprise — 16GB)**  
**Status:** Completed (System Information capture)

The Windows baseline was captured using the System Information tool prior to the OS wipe. **Idle RAM usage was not recorded**, but the following memory metrics were preserved from the screenshot and provide a valid baseline for comparison:

- **Installed Physical Memory (RAM):** 16 GB  
- **Total Physical Memory:** 15.7 GB  
- **Available Physical Memory:** 6.90 GB  
- **Total Virtual Memory:** 16.7 GB  
- **Available Virtual Memory:** 6.00 GB  

**Note:**  
Idle RAM usage was not captured before the OS migration. This does not impact the integrity of the project, as Fedora baseline and post‑upgrade metrics will serve as the primary comparison points.

---

### **Baseline RAM Usage (Fedora 43 — 16GB)**  
**Status:** Completed (live system capture)

Tools: `htop`, `free -g`

- **Total RAM:** 15 GB (system‑reserved difference from 16 GB is expected)  
- **Idle RAM usage:** 1 GB  
- **Free RAM:** 12 GB  
- **Available RAM:** 13 GB  
- **Swap usage:** 0 GB used / 7 GB total  

**Notes:**  
Fedora 43 running Sway TWM demonstrates an extremely low idle memory footprint. With only ~1 GB used at idle, this configuration is highly efficient and ideal for a hardened, minimal‑surface‑area ghost identity node.

---

### **Boot Time Comparison**  
**Status:** Fedora baseline captured, upgrade pending  

**Fedora 43 (16GB RAM) Boot Time Breakdown:**  
- **Firmware:** 7.539s  
- **Bootloader:** 2.790s  
- **Kernel:** 1.033s  
- **Initrd:** 14.960s  
- **Userspace:** 12.695s  
- **Total Boot Time:** **39.018s** to graphical.target  

**Notes:**  
The majority of the boot time is spent in firmware and initrd. Kernel and userspace times are efficient, and this provides a strong baseline for comparison after the 64GB RAM upgrade and post‑hardening service reductions.

---

### **CPU Load & Efficiency Metrics (Fedora 43 — 16GB)**  
**Status:** Completed (live system capture)

Tools: `top`, `htop`

**Idle CPU Load:**  
- **96.6% idle**  
- 1.4% user  
- 1.4% system  
- 0.7% I/O wait  

**Load Average:**  
- 1 min: 0.01  
- 5 min: 0.03  
- 15 min: 0.05  

**Task Summary:**  
- 357 total tasks  
- 1 running  
- 356 sleeping  
- 0 stopped  
- 0 zombie  

**Notes:**  
The system shows extremely low CPU utilization at idle, with near‑zero load averages and no background contention. This provides a clean baseline for comparison after the 64GB RAM upgrade and post‑hardening service reductions.

---

### **Power Efficiency & Thermal Behavior (Fedora 43 — 16GB)**  
**Status:** Completed (live system capture)

Tools: `sensors`, `powertop`

**Thermal Readings (Idle):**  
- **CPU Package Temperature:** 43°C  
- **Core Temperatures:** 37–41°C across active cores  

**Wakeups per Second:**  
- **283.7 wakeups/second** (GPU ops/sec and VFS ops/sec remained at 0.0)

**Idle Wattage:**  
Idle wattage could not be captured because the platform does not expose ACPI power telemetry to powertop. This is a known limitation on certain Dell business‑class systems. All other power‑efficiency metrics were successfully captured and provide a valid baseline.

---

### **Post‑Upgrade RAM Usage (Fedora 43 — 64GB)**  
**Status:** Pending hardware arrival  
**Expected Data:**  
- Idle RAM usage  
- Memory bandwidth improvements  
- Swap behavior changes  
- Stability and thermal characteristics  
- BIOS recognition and validation screenshots

This section will be updated once the 64GB RAM kit is installed and validated.

---

### **Security Posture Comparison (Planned)**  
This will be completed after Phase 3 (System Hardening).

Planned metrics:  
- Attack surface reduction  
- Disabled services count  
- SELinux audit logs  
- Firewall rule coverage  
- SSH hardening impact  
- Package footprint reduction  

---

### **Summary**  
This benchmark section will evolve as hardware upgrades and hardening phases are completed. The current baseline data provides a foundation for meaningful before‑and‑after comparisons once the 64GB RAM kit is installed and the system undergoes full hardening.

---

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
