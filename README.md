<h1 align="center">Cisco IOS Switch Command Cheat Sheet</h1>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow.svg"></a>
  <a href=https://www.netacad.com/><img src="https://img.shields.io/badge/Cisco-Networking-blue?logo=cisco&logoColor=white"></a>
  <a href=https://www.cisco.com/site/us/en/learn/training-certifications/certifications/enterprise/ccna/index.html><img src="https://img.shields.io/badge/CCNA-Study%20Guide-orange"></a>
  <a href=https://www.cisco.com/site/us/en/learn/training-certifications/tech-roles/network-engineer.html><img src="https://img.shields.io/badge/Role-Network%20Engineer-green"></a>
  <a href=https://github.com/hyprblaze><img src="https://img.shields.io/badge/Made%20by-HYPRBLAZE-purple?logo=github"></a>
</p>

<h4 align="center">📘 A Cisco IOS Switch Command Cheat Sheet for CCNA preparation and quick reference</h4>
Information is compiled from various official and community sources.  
Feel free to use this as a study aid or a handy guide when configuring or learning Cisco switch networking concepts. 🚀

### 🔑 Topics / Tags  
`Cisco` · `Networking` · `CCNA` · `Switching` · `IOS` · `Configuration` · `CheatSheet` · `VLAN` · `STP` · `Port Security` · `EtherChannel` · `SSH` · `VTP` · `Trunking`


---

## 📑 Table of Contents
- [Configuration Modes](#configuration-modes)

- [Important `show` Commands](#important-show-commands)

- [Filtering Information from `show` Commands](#filtering-information-from-show-commands)

- [Managing Multiple Interfaces](#Managing-Multiple-Interfaces)

- [VLANs](#VLANs)

- [Trunks](#Trunks)

- [VLAN Troubleshooting](#VLAN-Troubleshooting)

- [Voice VLANs](#Voice-VLANs)

- [SSH](#SSH)


---

## Configuration Modes

```bash
Switch>                # User EXEC mode
Switch> enable         # Privileged EXEC mode
Switch# configure terminal   # Global config mode
Switch(config)# interface fa0/1
Switch(config-if)# description Uplink-to-Router
```

---

## Important `show` Commands
```bash
show running-config        # Displays the active configuration in RAM
show startup-config        # Displays the saved config in NVRAM (loaded on boot)
show vlan brief            # Lists VLANs, names, status, and assigned ports
show interfaces status     # Shows interface status (UP/DOWN, VLAN, speed, duplex)
show mac address-table     # Displays learned MAC addresses and their ports
show spanning-tree         # Shows STP information (root bridge, port roles/states)
```

---
## Filtering Information from `show` Commands
```bash
show running-config | include vlan        # Show only lines containing "vlan"
show interfaces | begin GigabitEthernet0/1   # Display output starting from Gi0/1
show mac address-table | exclude dynamic  # Hide all lines with the word "dynamic"
```
---
## Managing Multiple Interfaces
```bash
interface range gi0/1 - 10     # Select multiple interfaces at once (Gi0/1 to Gi0/10)
switchport mode access         # Set all selected ports to access mode
switchport access vlan 20      # Assign VLAN 20 to all selected ports
```
---
## VLANs

### Creating VLANs
```bash
vlan 10              # Create VLAN 10
name VLAN10           # Assign a name ("VLAN10") to the VLAN
exit                 # Exit VLAN configuration mode
```
### Deleting VLANs
```bash
no vlan 10           # Delete VLAN 10
delete flash:vlan.dat   # Delete the entire VLAN database from flash
```
### Assigning Interfaces to a VLAN
```bash
interface gi0/1             # Enter interface Gi0/1
switchport mode access       # Set port as access
switchport access vlan 10    # Assign VLAN 10 to the port
```
---
## Trunks

### Configuring Trunks
```bash
interface gi0/24                          # Enter trunk interface (Gi0/24)
switchport mode trunk                     # Set port as trunk
switchport trunk allowed vlan 10,20,30    # Allow only VLANs 10, 20, and 30
switchport trunk native vlan 99           # Set VLAN 99 as the native VLAN
```
### Dynamic Trunking Protocol (DTP)
```bash
switchport mode dynamic desirable   # Actively try to form a trunk
switchport mode dynamic auto        # Passively form a trunk if other side is trunk/desirable
switchport nonegotiate              # Disable DTP negotiation
```
---
## VLAN Troubleshooting
```bash
show vlan brief             # Display all VLANs and their assigned ports
show interfaces trunk       # Verify trunk ports and allowed VLANs
show mac address-table      # View MAC addresses learned on the switch
show running-config         # Check VLAN and interface configurations
```
---
## Voice VLANs

```bash
interface gi0/5              # Enter interface Gi0/5
switchport mode access       # Set port as access
switchport access vlan 10    # Assign VLAN 10 for data
switchport voice vlan 20     # Assign VLAN 20 for voice traffic (IP phones)
```
---
## SSH

### Initial SSH Setup
```bash
hostname Switch1                        # Set device hostname  
ip domain-name example.com              # Define domain name (needed for RSA key)  
crypto key generate rsa                 # Generate RSA keys for SSH  
username admin privilege 15 secret cisco123   # Create local admin user  
line vty 0 4                            # Enter VTY line configuration (remote access)  
 transport input ssh                    # Allow only SSH (disable Telnet)  
 login local                            # Use local user database for login  
```
### Modifying SSH Config
```bash
ip ssh version 2                        # Enable SSH version 2 (more secure)  
ip ssh time-out 60                      # Set SSH idle timeout to 60 seconds  
ip ssh authentication-retries 3         # Allow max 3 login attempts  
```
---
## Port Security

### Dynamic Port Security  
```bash
interface gi0/2                              # Enter interface  
switchport mode access                       # Set interface to access mode  
switchport port-security                     # Enable port security  
switchport port-security maximum 2           # Allow max 2 MAC addresses  
switchport port-security violation shutdown  # Shutdown port if violation occurs  
```
### Sticky Port Security
```bash
interface gi0/2                              # Enter interface  
switchport port-security mac-address sticky  # Learn & save MAC addresses dynamically  
```
