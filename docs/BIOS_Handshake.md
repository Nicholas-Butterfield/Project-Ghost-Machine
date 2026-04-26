# BIOS Configuration & Linux Hardware Handshake

One of the primary challenges in hardening the Dell Latitude 5430 for Linux was overcoming factory BIOS settings optimized for Windows-only environments.

## 1. Storage Controller: RAID to AHCI/NVMe
- **Issue:** The Linux kernel and LUKS encryption layer could not "see" the Crucial P5 Plus SSD.
- **Cause:** Dell's default "RAID On" mode utilizes Intel Rapid Storage Technology (RST), which requires proprietary Windows drivers.
- **Solution:** Switched to **AHCI/NVMe** mode. 
- **Impact:** This provides the Linux kernel direct block-level access to the NVMe controller, which is a requirement for stable Full Disk Encryption (FDE).

## 2. Wireless Interface: PCIe to USB Bus Mode
- **Issue:** The Intel AX211 Wi-Fi 6E card was powered but "Hard Blocked" or invisible to the OS.
- **Cause:** Modern Latitude motherboards use a hybrid PCIe/USB bus for the M.2 wireless slot. Windows handles the PCIe power-state transitions, whereas Linux often expects a standard USB-interface handshake for combo cards (Wi-Fi/Bluetooth).
- **Solution:** Reconfigured the **Wireless/WWAN interface bus mode** to **USB**.
- **Impact:** Immediate initialization of the 6GHz radio bands and stable Bluetooth connectivity.

## 3. Dell SafeBIOS & Secure Boot
- **Issue:** Occasional "Hangs" during the transition from the Dell Splash screen to the LUKS decryption prompt.
- **Solution:** Disabled **Secure Boot** and set POST Behavior to **Thorough**.
- **Impact:** Ensures the BIOS fully initializes all hardware (specifically the TPM and NVMe controller) before handing control to the GRUB bootloader.
