# Security Lab

Team: RUSCH & MEISL

## Infos

* Proxmox VE
* Three network zones: LAN - DMZ - ATTACK
* Real internet is blocked by the edge firewall
* ATTACK simulates Internet access
* IPv4 only
* RAID1 - 2x500GB
* SIEM/EDR: Wazuh
* Firewall: pfSense
* Vulnerable Web app: Damn Vulnerable WordPress


## Network Plan

![](https://i.imgur.com/CHObiub.png)

Router:
* vmbr1 - LAN: 10.0.10.1
* vmbr2 - DMZ: 10.0.20.1
* vmbr3 - ATTACK: 10.0.30.1
* vmbr0: 192.168.0.1

LAN:
* 10.0.10.0/24
* Win: 10.0.10.10
* SIEM: 10.0.10.20
* Debian: 10.0.10.30

DMZ:
* 10.0.20.0/24
* Web: 10.0.20.10

ATTACK:
* 10.0.30.0/24
* Kali: 10.0.30.10

## Device Overview

| Name   | IP                                           | OS                  | Dienste                                        | UPDATE | URL                |
| ------ | -------------------------------------------- | ------------------- | ---------------------------------------------- | ------ | ------------------ |
| Router | 10.0.10.1/ 10.0.20.1/ 10.0.30.1/ 192.168.0.1 | Ubuntu 24.4 server  | NAT, DNS (bind)                                | Ja     |                    |
| Kali   | 10.0.30.10                                   | Kali Linux          | BurpSuite, Metasploit, Nessus, Nmap, Wireshark | Ja     |                    |
| Web    | 10.0.20.10                                   | Windows Server 2008 | DVWP, XAMPP                                    | Nein   | http://10.0.10.20  |
| Win7   | 10.0.10.10                                   | Windows 7           | telnet, rdp                                    | Nein   |                    |
| SIEM   | 10.0.10.20                                   | Ubuntu 24.4 server  | Docker, Wazuh                                  | Ja     |                    |
| Debian | 10.0.10.30                                   | Debian 7.11         | telnet, ftp                                    | Nein   |                    |
