# Wraynet Windows Utility

**A comprehensive Windows 11 deployment and management suite for IT technicians.**
**Vibed by Kyran Wray** — *v2.0 (May 2026)*

---

## ## Overview

**Wraynet Windows Utility** is a PowerShell-based ecosystem designed to streamline the setup, "sanitization," and maintenance of Windows 11 machines. While optimized for HP laptops and desktops in NZ school environments, it is a universal tool for any technician looking to reclaim performance and privacy from modern Windows installs.

The repository consists of three primary execution modes:

1. **WraynetUtility.ps1 (The GUI):** The full dark-themed management console.
2. **TotalDeploy-Standalone.ps1 (The Provisioner):** A CLI-guided full deployment sequence.
3. **QuickSanitize.ps1 (The Headless Script):** A "scorched-earth" debloat and tweak script for rapid runs.

---

## ## Requirements

* **OS:** Windows 10 / 11
* **Privileges:** Must be run as **Administrator**
* **Environment:** PowerShell 5.1+
* **Dependencies:** Winget (Windows Package Manager)

---

## ## Repository Components

### 1. Wraynet Windows Utility (GUI)

The flagship tool. It wraps complex management tasks into a clean, actionable interface.

* **Info Panel:** Live system data (CPU, RAM, Uptime). Click fields to trigger actions (e.g., click "COMPUTER" to rename).
* **Application Provisioning:** Checkbox-based installer for Chrome, Office, VLC, 7-Zip, Adobe, and more. Includes automatic uBlock Origin deployment for Firefox.
* **Network Manager:** Static IP/DHCP configuration and DNS management.
* **Domain Tools:** Join/Leave domains, Azure AD status, and GPReport generation.
* **Printer Setup:** Add network printers via IP (RAW/LPR/IPP) with `.inf` driver support.
* **Diagnostics:** Battery reports, SMART disk health, and Windows Update repair tools.

### 2. Total Deploy (Standalone CLI)

Designed for rapid-fire provisioning where a GUI isn't desired but user input is still needed. It walks the tech through a linear path:

> **Rename** → **Local Account** → **Domain Join** → **Activation** → **Vendor Purge** → **Debloat** → **Apps** → **Restart**

### 3. QuickSanitize (Headless)

The "Sanity" script. It runs with zero UI, making it perfect for remote execution or deployment via USB.

* **Microsoft Purge:** Removes 30+ bloatware apps including Copilot, Teams, and Xbox.
* **Vendor Purge:** Auto-detects HP, Dell, Lenovo, etc., and nukes manufacturer bloat (e.g., HP Wolf Security).
* **Essential Tweaks:** Restores Win10 Right-Click menu, aligns Taskbar to the left, hides Bing from Start, and kills telemetry.

---

## ## Key System Tweaks (Included in all scripts)

* **Privacy:** DiagTrack service disabled; Advertising IDs and tailored experiences killed.
* **UI:** Taskbar cleaned (Copilot, Widgets, Task View removed); File extensions forced to "Visible."
* **Performance:** Hibernation disabled; Edge startup boost and background modes terminated.
* **Automation:** OneDrive and Teams autostart blocked via policy; User folders redirected away from OneDrive back to local disk.
* **Localization:** Timezone forced to **New Zealand Standard Time**.

---

## ## Getting Started

### Installation

Clone the repository or download the `.ps1` files to a technician's USB drive.

### Execution

Right-click any script and select **Run with PowerShell**. If blocked by execution policy, run this command once:

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned -Force

```

### Compiling to EXE

To create a standalone portable tool with an embedded manifest for Admin rights:

```powershell
Install-Module ps2exe -Scope CurrentUser -Force
ps2exe .\WraynetUtility.ps1 .\WraynetUtility.exe -requireAdmin -noConsole

```

---

## ## Customization Guide

| Target | Location in Script |
| --- | --- |
| **Default Product Key** | Search `DEFAULT KEY` |
| **App Install List** | `AP-Check` entries in `Show-AppPicker` |
| **Vendor Bloat Lists** | `$vendorBloat` and `$vendorWinget` hashtables |
| **Active Hours** | `ActiveHoursStart` / `ActiveHoursEnd` in tweaks section |

---

## ## Notes

* **Errors:** Some AppX packages (like "People") are stubborn on Education builds; these errors are non-fatal.
* **Explorer:** The script will automatically restart `explorer.exe` to apply registry changes (Taskbar alignment, Context menu).
* **Disclaimer:** This tool is built for NZ school IT environments. Not affiliated with Microsoft, HP, or any other hardware vendor.--------------------------------------------------------------
Total Deploy — Standalone

A full-spectrum, CLI-only provisioning sequence for rapid Windows workstation deployment.
## Overview

This script is the automated "sanitizer" and "provisioner" for fresh Windows builds. It removes the need for a GUI by walking through a linear deployment sequence directly in the terminal. It handles everything from system naming to core software installation.
## Deployment Sequence

    Rename Computer: Prompts for a new hostname (max 15 chars).

    Local Account: Optional creation of a local user with Administrator or Standard rights.

    Domain Join: Staged domain join (completes after the final reboot).

    Activation: Checks license status and allows for manual product key entry.

    Vendor Purge: Scans for manufacturer bloatware (HP, Dell, Lenovo, etc.) and nukes it.

    MS Debloat: Removes non-essential Windows Store apps (Xbox, Teams, News, etc.).

    Essential Tweaks:

        Kills telemetry and ads.

        Disables Bing in the Start menu and Widgets on the taskbar.

        Restores the Windows 10 right-click menu.

        Sets timezone to NZ Standard Time.

    App Installation: Uses winget to install a core software stack:

        Office, Chrome, Firefox, Google Drive, VLC, 7-Zip, and Adobe Reader.

## Core Defaults

    Update Hours: Set to 8:00 AM – 5:00 PM to prevent reboots during work hours.

    File Explorer: File extensions are set to visible by default.

    Power: Hibernation is disabled to save disk space.

    Defaults: Automatically attempts to set Chrome as the default browser and VLC as the default media player for common file types.
--------------------------------------------------------------




SYSTEM SANITIZE
---------------------------------------------------------------

A scorched-earth PowerShell script to reclaim Windows from bloatware, telemetry, and questionable UI decisions.
## What it Does

This script automates the "sanitization" of a fresh Windows install (or a cluttered one) by targeting four main areas:

    MS Bloat Removal: Uninstalls pre-installed junk like News, Weather, Xbox, Solitaire, and Copilot using AppX and Winget.

    Vendor Purge: Detects your hardware (HP, Dell, Lenovo, etc.) and hunts down manufacturer-specific "Support Assistants" and bloat.

    Essential Tweaks: Restores the Windows 10 style left-aligned taskbar, brings back the classic right-click menu, and disables Bing in the Start menu.

    Privacy Lockdown: Kills telemetry, prevents Edge from "optimizing" (spying), and stops OneDrive/Teams from hijacking your startup and file paths.

## Key Modifications

    Explorer: Shows file extensions by default (no more guessing).

    Storage: Redirects User folders (Desktop, Documents, etc.) away from OneDrive back to local storage.

    Updates: Sets active hours to 8 AM – 5 PM to prevent mid-work reboots.

    Timezone: Automatically syncs to NZ Standard Time.

