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
---

## ⚙️ Configuration Modes
```bash
Switch>                # User EXEC mode
Switch> enable         # Privileged EXEC mode
Switch# configure terminal   # Global config mode
Switch(config)# interface fa0/1
Switch(config-if)# description Uplink-to-Router
```

---

## 🔎 Important `show` Commands
```bash
show running-config        # Displays the active configuration in RAM
show startup-config        # Displays the saved config in NVRAM (loaded on boot)
show vlan brief            # Lists VLANs, names, status, and assigned ports
show interfaces status     # Shows interface status (up/down, VLAN, speed, duplex)
show mac address-table     # Displays learned MAC addresses and their ports
show spanning-tree         # Shows STP information (root bridge, port roles/states)

