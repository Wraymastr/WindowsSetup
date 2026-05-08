--------------------------------------------------------------
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

