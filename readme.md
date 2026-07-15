# Cybersecurity Home Lab Documentation

## 1. Introduction
This lab environment was built to conduct penetration testing and vulnerability assessments in a safe, isolated sandbox. Using Oracle VirtualBox, a Kali Linux instance acts as the attacking machine targeting an intentionally vulnerable Metasploitable 2 instance.

## 2. Objectives
- Design and configure an isolated virtual network environment.
- Conduct network reconnaissance and active scanning using Nmap.
- Analyze service vulnerabilities and map potential attack vectors.
- Perform targeted exploitation using the Metasploit Framework.

## 3. Lab Environment Overview
### Hardware
- **Host Machine**: Multi-core CPU, 8GB+ RAM

### Software & Tools
- **VirtualBox**: Type-2 virtualization hypervisor.
- **Kali Linux**: Offensive security distribution containing reconnaissance and exploitation tools.
- **Metasploitable 2**: Intentionally vulnerable Linux-based VM used as the target environment.
- **Nmap**: Network mapper for port scanning and service version detection.
- **Metasploit Framework**: Penetration testing platform used for automated exploit verification.

## 4. Network Setup and Isolation
To ensure absolute isolation and prevent exposing vulnerable services to the host's physical network, both virtual machines were configured on a private **NAT Network** (or **Host-Only Adapter**) within VirtualBox.

- Verified IP allocation on the same subnet using `ifconfig` on both machines.
- Confirmed internal network connectivity via `ping`.
- Executed reconnaissance scans from the Kali instance using Nmap:
  - `nmap -sS -sV -A <target-IP>`: Performed a stealthy TCP SYN scan, probed open ports for service/version details, and ran OS detection.

## 5. Exploitation & Verification
Using the reconnaissance data gathered from Nmap, the target's open ports and running services were cross-referenced against known vulnerabilities.

1. Initialized the Metasploit console on Kali using `msfconsole`.
2. Loaded the target exploit module (e.g., `exploit/unix/ftp/vsftpd_234_backdoor`).
3. Configured the payload options and set `RHOSTS` to the target IP address.
4. Executed the exploit to successfully obtain an interactive root shell interface on the target.

