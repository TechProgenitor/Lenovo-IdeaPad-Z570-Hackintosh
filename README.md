<img src="https://github.com/user-attachments/assets/e03b1e42-6e5b-42c6-b483-62d5bb82bad3" width="497" height="349">

[![](https://img.shields.io/badge/Bootloader-OpenCore_1.0.2_RELEASE-blue)](https://github.com/acidanthera/OpenCorePkg/releases/tag/1.0.2) [![](https://img.shields.io/badge/macOS-Sequoia%2015.0.1-148F77)](https://apps.apple.com/us/app/macos-sequoia/id6596773750?mt=12) [![](https://img.shields.io/badge/Lenovo-IdeaPad%20Z570-1F618D)](https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/ideapad-z-series-laptops/ideapad-z570)

# Please Note

This laptop natively supports up to macOS High Sierra. If you plan to install a more modern OS, you'll need to run [OpenCore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher/releases) after installation to fix the GPU acceleration.

NVIDIA Optimus is not supported on macOS. Therefore, the discrete graphics have been disabled specifically for macOS using SSDT-NoHybGfx. Thanks to this SSDT, you can set "Graphic Device" to "Optimus" in the BIOS settings, and use the discrete graphics on your other operating systems.

Enable "USB Legacy" in the BIOS before installation, and connect your bootable flashdrive to one of the four USB 2.0 ports.

Set "SATA Controller Working Mode" to "AHCI" in the BIOS to avoid a prohibited symbol when booting macOS from the internal drive.

This repo has an SSDT-PM that's designed for the Intel Core i5-2430M. If you have a different CPU model, you'll need to generate a new SSDT-PM with [ssdtPRGen.sh](https://github.com/Piker-Alpha/ssdtPRGen.sh) and replace the existing file within the ACPI folder.

# Specifications

| Hardware | Lenovo IdeaPad Z570 |
| ------------- | ------------- |
| CPU | Intel Core i5-2430M |
| GPU | Intel HD Graphics 3000<br>NVIDIA GeForce GTX 520M |
| Chipset | Intel HM65 Express Chipset |
| Memory | 2x - Samsung M41B5273CH0-CH9<br>4GB DDR3 1333MHz |
| USB | Intel 6 Series/C200 Series Chipset |
| WiFi/BT | Intel Centrino Wireless N-1000 |
| LAN | Realtek RTL8100 |
| Audio | Realtek ALC272 |
| Card Reader | Realtek RTS5139|

# Issues
| | |
| --- | --- |
| WiFi/Bluetooth Don't Work | Requires somehow modifying the BIOS to remove the WLAN/WWAN whitelist. Alternatively, you can enable wireless functionality with a USB WiFi Adapter. |
| VGA output remains connected after disconnecting from an external monitor and running "Detect Displays" | This has something to do with the framebuffer patch and/or ACPI methods. Putting the computer to sleep and waking it up forces macOS to re-enumerate all video ports, disconnecting the VGA output, and resolving the issue.<br><br>Closing the laptop lid won't trigger sleep if macOS still detects an external VGA monitor. You'll need to use the Fn+F1 keyboard shortcut, or select "Sleep" from the Apple menu. |