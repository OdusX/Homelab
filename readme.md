# Cybersecurity Home Lab Documentation

## 1. Introduction

This lab was created to practice penetration testing in a safe, controlled environment using VirtualBox. Kali Linux was used as the attacker machine and Metasploitable as the vulnerable target.

## 2. Objectives

- Learn and practice penetration testing tools and techniques.
- Understand vulnerability scanning and exploitation.
- Explore network scanning and reconnaissance with Nmap.
- Use Metasploit framework for automated exploitation.

## 3. Lab Environment Overview

**Hardware**
- Host machine with 8GB RAM and multi-core CPU.

**Software**
- **VirtualBox:** Virtualization platform to run multiple VMs.
- **Kali Linux:** Attacker OS with pre-installed pentesting tools.
- **Metasploitable 2:** Intentionally vulnerable Linux VM for exploitation practice.
- **Nmap:** Network scanner included in Kali Linux.
- **Metasploit Framework:** Exploitation framework included in Kali Linux.

## 4. Network Setup and Connectivity Testing

To ensure Kali Linux and Metasploitable could communicate, both VMs were configured to be on the same virtual network in VirtualBox. This was done using the Bridged Adapter in the VirtualBox network settings and assigning both VMs to it. This setup mimics a local network environment, allowing the VMs to see each other without exposing them to external networks.

- Verified both VMs received IP addresses in the same subnet by running `ifconfig` on each machine.
- Confirmed network connectivity by pinging Metasploitable’s IP address from Kali Linux.
- Used Nmap from Kali to scan Metasploitable, successfully detecting open ports and services:
  - `-sS`: TCP SYN Scan, performs a quick port scan by sending a TCP SYN packet to the target port but does not complete the TCP handshake.
  - `-sV`: Service version detection, probes open ports to determine what services and versions are running.
  - `-A`: Aggressive scan, provides comprehensive information about the target system.

This network configuration aligns with best practices to keep vulnerable VMs isolated yet reachable for penetration testing.

## 5. Tools and Usage

| Tool           | Purpose                                         |
|----------------|-------------------------------------------------|
| Nmap           | Scan Metasploitable for open ports and services.|
| Metasploit     | Exploit vulnerabilities found on Metasploitable.|
| Kali Linux     | Platform hosting pentesting tools.              |
| Metasploitable | Vulnerable target machine for practice.         |

## 6. Exercise: Gaining Access with Metasploit

- Launched Metasploit framework on Kali using `msfconsole`.
- Used and configured an exploit module targeting a vulnerable service found on Metasploitable.
- Successfully exploited the target and gained shell access, demonstrating the lab’s effectiveness for penetration testing practice.

## 7. Resources

- [VirtualBox installation](https://youtu.be/homRENM8KVY?si=UOJwnH2dGWu_lQWt)
- [Kali Linux installation](https://youtu.be/ZJFu0AoAY_g?si=Tsk7mOIEhwVa4Erf)
- [Metasploitable installation](https://youtu.be/l8v65ePR44k?si=79qG8FQOYxkq3LRH)