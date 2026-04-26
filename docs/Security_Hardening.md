# Security Hardening & Identity Management

This document outlines the security policies and encryption standards implemented on the Ghost Machine to ensure privacy and data integrity.

## 1. Data at Rest (DAR): LUKS Encryption

* **Standard:** LUKS2 (Linux Unified Key Setup)
* **Implementation:** Full Disk Encryption (FDE) was applied during the Fedora installation phase.
* **Logic:** By encrypting the 1TB Crucial P5 SSD at the partition level, the data remains inaccessible even if the physical hardware is compromised. This requires a pre-boot passphrase before the kernel is initialized.

## 2. Identity & PII Reduction

* **User Alias:** `subrootghost`
* **Logic:** To minimize Personally Identifiable Information (PII) within system logs, terminal metadata, and potential screen captures during technical labs, a generic identity was established.
* **Security Impact:** Reduces the digital footprint of the primary operator during network-facing activities and lab documentation.

## 3. Physical Security (TPM 2.0)

* **Hardware:** Integrated Trusted Platform Module 2.0.
* **Role:** Working in tandem with the BIOS hardening, the TPM ensures that the boot process hasn't been tampered with before the LUKS decryption prompt appears.

## 4. Network Hardening & Attack Surface Reduction

This section details the transition from "Workstation Default" to a "Hardened Lab" posture.

### **4.1 Firewall Policy (Default Deny)**
* **Observation:** The default `FedoraWorkstation` zone allowed wide-open access to high ports (1025-65535).
* **Action:** - Removed `1025-65535/tcp` and `1025-65535/udp`.
    - Removed `samba-client` to prevent unauthenticated protocol exposure.
* **Result:** Attack surface restricted to essential services only (`ssh`, `dhcpv6-client`).

### **4.2 Service Audit & Remediation**
* **Service:** `cups` (Common Unix Printing System)
    - **Action:** Stopped and Disabled (`systemctl disable --now cups`).
    - **Logic:** Printing services are unnecessary for a mobile cybersecurity lab and present a legacy vulnerability vector.
* **Protocol:** `LLMNR` (Port 5355)
    - **Status:** Identified as active via `ss -tulpn`. 
    - **Risk:** Vulnerable to spoofing/poisoning attacks.

### **4.3 Resolution of Persistent Services (mDNS/LLMNR)**
- **Post-Configuration Audit:** Identified orphan `avahi-daemon` processes bypasssing initial `systemctl stop` commands.
- **Remediation:** - Manually terminated PID 60254 (`SIGKILL`).
    - Configured NetworkManager connection `Alpha1-6G` to `connection.mdns no`.
    - Explicitly defined `LLMNR=no` and `MulticastDNS=no` in `/etc/systemd/resolved.conf`.
- **Validation:** Confirmed zero listeners on 5353/UDP and 5355/UDP post-reboot.
  
---

## 5. Audit Log & Version History

| Date | Action | Performed By |
| :--- | :--- | :--- |
| 2026-04-25 | Initial Network Audit (`ss`, `firewall-cmd`) | subrootghost |
| 2026-04-25 | Closure of 1025-65535 port ranges | subrootghost |
| 2026-04-25 | Decommissioning of CUPS service | subrootghost |
