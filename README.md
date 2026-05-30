
# macOS MDM Bypass Script

A lightweight utility script designed to bypass Mobile Device Management (MDM) enrollment profiles during the initial macOS setup phase.

## ?? How It Works

The script executes the following operations from macOS Recovery Mode:
1. **Auto-Detects Volumes:** Dynamically finds your macOS System and Data volumes.
2. **Creates a Local Admin Account:** Generates a temporary administrative user (`Apple` / `1234` by default) to allow setup completion.
3. **Blocks MDM Domains:** Appends official Apple enrollment domains to the local `/etc/hosts` file (`0.0.0.0`), preventing the device from phoning home.
4. **Clears Cloud Configs:** Removes local activation records and triggers bypass flags (`.AppleSetupDone`).

---

## ?? Quick Start Guide

### Step 1: Boot into Recovery Mode
* **Apple Silicon (M1/M2/M3):** Turn off your Mac. Press and hold the **Power button** until you see "Loading startup options." Click Options, then click Continue.
* **Intel Mac:** Turn off your Mac. Press the Power button and immediately hold down **Command + R** until the Apple logo appears.

### Step 2: Open Terminal
1. Ensure you are connected to Wi-Fi.
2. In the top menu bar, go to **Utilities** > **Terminal**.

### Step 3: Run the Script
Copy and paste the following command into the Terminal window and press Enter:

```bash
curl -L [https://raw.githubusercontent.com/esslm/mdm/main/bypass-mdm-v2.sh](https://raw.githubusercontent.com/esslm/mdm/main/bypass-mdm-v2.sh) -o bypass-mdm.sh && chmod +x ./bypass-mdm.sh && ./bypass-mdm.sh

```

### Step 4: Complete the Setup Wizard

1. Select **Option 1** ("Bypass MDM from Recovery").
2. Follow the prompts to create your temporary account (or press **Enter** to accept the default user `Apple` with password `1234`).
3. Once finished, close Terminal and **Reboot** your Mac.

---

## ?? Post-Bypass Actions

1. Log into macOS using the temporary account credentials.
2. Skip all initial setup screens (Apple ID, Touch ID, Location Services).
3. Navigate to **System Settings > Users & Groups** and create your permanent administrative account.
4. Log out of the temporary account, sign into your new permanent account, and delete the temporary `Apple` profile.

---

## ?? Disclaimer

This script is provided for educational and administrative recovery purposes on personally owned hardware. It modifies local configuration files to prevent device management check-ins; however, the device serial number remains registered within the provisioning organization's cloud portal database. Use responsibly.

