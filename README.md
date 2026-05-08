WRAYNET SYSTEM SANITIZE
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

