# Security Hardening & Identity Management

This document outlines the security policies and encryption standards implemented on the Ghost Machine to ensure privacy and data integrity.

## 1. Data at Rest (DAR): LUKS Encryption
- **Standard:** LUKS2 (Linux Unified Key Setup)
- **Implementation:** Full Disk Encryption (FDE) was applied during the Fedora installation phase.
- **Logic:** By encrypting the 1TB Crucial P5 SSD at the partition level, the data remains inaccessible even if the physical hardware is compromised. This requires a pre-boot passphrase before the kernel is initialized.

## 2. Identity & PII Reduction
- **User Alias:** `subrootghost`
- **Logic:** To minimize Personally Identifiable Information (PII) within system logs, terminal metadata, and potential screen captures during technical labs, a generic identity was established.
- **Security Impact:** Reduces the digital footprint of the primary operator during network-facing activities and lab documentation.

## 3. Physical Security (TPM 2.0)
- **Hardware:** Integrated Trusted Platform Module 2.0.
- **Role:** Working in tandem with the BIOS hardening, the TPM ensures that the boot process hasn't been tampered with before the LUKS decryption prompt appears.
