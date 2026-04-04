# Security Lab

Team: RUSCH & MEISL

## Infos

* Proxmox VE
* Four network zones: LAN - DMZ - ATTACK - MGMT
* Real internet is blocked by the edge firewall
* ATTACK simulates Internet access
* IPv4 only
* RAID1 - 2x500GB
* SIEM/EDR: Wazuh
* Firewall: pfSense
* Vulnerable Web app: Damn Vulnerable WordPress

## Network Plan

![Network plan](https://i.imgur.com/FoEXwDW.png)

## Device Overview

| Name         | IP                                          | OS                         | Services                                       | Username      | UPDATE | URL               |
| ------------ | ------------------------------------------- | -------------------------- | ---------------------------------------------- | ------------- | ------ | ----------------- |
| pfSense      | 10.0.10.1/ 10.0.20.1/ 10.0.30.1/ 10.0.40.1 / 192.168.0.1      | FreeBSD  | NAT, DNS (bind)                                | root          | Yes    |                   |
| Kali         | 10.0.30.10                                  | Kali Linux                 | BurpSuite, Metasploit, Nessus, Nmap, Wireshark | kali          | Yes    |                   |
| Web          | 10.0.20.10                                  | Windows Server 2008        | DVWP, XAMPP                                    | Administrator | No     | http://10.0.10.20 |
| Win7         | 10.0.10.10                                  | Windows 7                  | telnet, rdp                                    | user          | No     |                   |
| Debian       | 10.0.10.30                                  | Debian 7.11                | telnet, ftp                                    | debian        | No     |                   |
| SIEM         | 10.0.40.10                                  | Ubuntu 24.4 server         | Docker, Wazuh                                  | ubuntu        | Yes    |                   |
| Manager      | 10.0.40.20                                  | Ubuntu 24.04.4 LTS desktop |                                                | ubuntu        | Yes    |                   |
