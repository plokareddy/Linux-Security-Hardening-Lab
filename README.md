# Linux-Security-Hardening-Lab

## Project Overview
Linux Security Hardening Lab is a hands-on security assessment and hardening project performed on an Ubuntu virtual machine running on macOS. The project covers network discovery, traffic analysis, security auditing, vulnerability assessment, firewall hardening, malware detection, and final security validation. The goal was to evaluate the system's security posture, identify vulnerabilities, implement security controls, and validate security improvements.

## Tools Used
- Ubuntu Linux
- Wireshark
- Nmap
- Lynis
- UFW
- Rkhunter
  
## Project Phases 
1.  Environment setup & Network Discovery
2.  Traffic Analysis 
3.  Security Auditing with Lynis tool 
4.  Vulnerability Assessment
5.  Authentication Log Review 
6.  Firewall Hardening 
7.  File Permission Review 
8.  Service Hardening 
9.  Malware and rootkit Detection 
10. System Updates and Patching 
11. Final Security audit/validation

##  Phase 1:Environment setup & Network Discovery
### Objective 
The objective of this phase is to understand the network configuration of the Ubuntu virtual machine before beginning the security asessment 
### Commands used 
ip a
### Findings 
It contained the network and loopback interface of assigned IPv4 ans IPv6 addresses 
### Security Relevance
Identifying network interfaces is important because it helps security analysts understand how a system communicates on a network and provides a foundation for further traffic analysis. 

