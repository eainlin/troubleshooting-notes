# ESXi Management Agent Restart Guide\
### Date: 11-Jun-2026
### Author: Htoo Eain Lin

## Issue

* “VXR0100A0 ALARM Unable to Communicate with host”
* “Cannot synchronize host ygn-ssc-esxi-01 [sschospital.com](http://sschospital.com/)”
* “Please refresh your browser.”

## Solution: Restart ESXi Management Agents via DCUI

1. **Access ESXi Console**

   * Connect a monitor and keyboard to your ESXi host.
   * You will see the yellow/grey ESXi console.

2. **Login to ESXi**

   * Press `F2` → `Customize System / View Logs`
   * Enter **root username** and **password**

3. **Navigate to Troubleshooting Options**

   * Use arrow keys → `Troubleshooting Options` → Press `Enter`

4. **Restart Management Agents**

   * Options available:

     * Enable ESXi Shell
     * Enable SSH
     * Restart Management Agents ✅
   * Select **Restart Management Agents** → Press `Enter`
   * Confirm with `F11`
   * Warning: vCenter/clients may lose connection temporarily.

5. **Exit Console**

   * Wait a few seconds for services to restart → Press `Esc` to exit

6. **Verify**

   * Try logging into the ESXi Web UI again from your browser

✅ Note: This does **NOT** affect your running VMs.
