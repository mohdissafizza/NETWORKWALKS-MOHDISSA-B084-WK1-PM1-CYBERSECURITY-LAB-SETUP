# NETWORKWALKS-MOHDISSA-B084-WK1-PM1-CYBERSECURITY-LAB-SETUP
## Project Overview
This project focuses on setting up a virtual cybersecurity and penetration-testing laboratory using VirtualBox and Kali Linux. The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, vulnerability assessment and other security-testing activities can be performed safely.
The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

## Lab Specifications
* **Skill:** Cybersecurity
* **Virtualization:** VirtualBox
* **Guest OS:** Kali Linux
* **Network Type:** Custom NAT Network (`10.0.0.0/24`)
* **Static IP Address:** `10.0.0.2`
* **Subnet Mask:** `255.255.255.0` (`/24`)
* **Gateway:** `10.0.0.1`
* **DNS Server:** `10.0.0.1`

## Step-by-Step Implementation
1. **VirtualBox NAT Network Setup:** 
   * Created a custom `NatNetwork` (`10.0.0.0/24`) to isolate the virtual machine while allowing controlled external access.
2. **Kali Linux OS Installation:** 
   * Installed Kali Linux on a dedicated virtual hard drive, setting up user accounts and disk partitioning.
3. **Network Adapter Configuration:** 
   * Enabled the network adapter and ensured the virtual cable was connected in VirtualBox settings.
4. **Static IP Configuration:** 
   * Configured `Wired connection 1` with a static IP (`10.0.0.2`), gateway (`10.0.0.1`), and DNS (`10.0.0.1`).
5. **Environment Preservation:** 
   * Took a clean snapshot of the virtual machine to allow quick rollbacks for future lab modules.

## Troubleshooting
* **Issue:** Loss of internet connectivity after applying the static IP due to a NetworkManager timeout behavior.
* **Solution:** Applied the `nmcli` workaround via the terminal to adjust the timeout setting and restart the network interface:
  ```bash
  sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
  sudo nmcli connection down "Wired connection 1"
  sudo nmcli connection up "Wired connection 1"

