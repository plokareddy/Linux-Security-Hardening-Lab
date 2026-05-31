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
## Phase 2: Traffic Analysis
### Objective
The objective of this phase was to capture and analyze network traffic to understand how data travels between the system and external hosts.
### Commands Used
ping google.com
### Findings
ICMP Echo Request and Echo Reply packets were successfully captured using Wireshark. The packet details showed source and destination IP addresses, packet sequence numbers, and Time-To-Live (TTL) values. This confirmed successful network communication between the Ubuntu virtual machine and an external host.
### Security Relevance
Network traffic analysis helps security analysts understand normal network behavior and identify suspicious communications. Packet captures can be used during incident investigations to detect malicious activity, unauthorized connections, and unusual traffic patterns.
## Phase 3: Security Auditing with Lynis
### Objective
The objective of this phase was to perform a security audit of the Ubuntu system and identify potential weaknesses, misconfigurations, and areas for improvement.
### Commands Used
sudo lynis audit system
### Findings
The Lynis audit completed successfully and performed over 240 security tests on the system. The initial hardening index score was 67. The audit identified areas where security could be improved, including the absence of intrusion detection and malware scanning software.
### Security Relevance
Security auditing tools such as Lynis help identify weaknesses that may increase risk to a system. Regular audits provide visibility into security posture and help administrators prioritize hardening efforts to reduce the attack surface.
## Phase 4: Vulnerability Assessment
### Objective
The objective of this phase was to identify open ports and exposed services on the system that could potentially increase the attack surface.
### Commands Used
nmap localhost
### Findings
An Nmap scan was performed against the local system. The results showed that the host was active and only one TCP port (631/tcp) was open. The service running on this port was identified as IPP (Internet Printing Protocol). The remaining 999 scanned ports were closed.
### Security Relevance
Port scanning helps security analysts identify services that are exposed on a system. Understanding which ports are open is important for reducing attack surface and ensuring that only necessary services are available to users and applications.
## Phase 5: Authentication Log Review
### Objective
The objective of this phase was to review authentication and system logs to understand how administrative actions and security-related activities are recorded on a Linux system.
### Commands Used
cat /var/log/auth.log
### Findings
The authentication logs recorded multiple administrative actions performed during the assessment. The logs showed sudo privilege escalation events, UFW firewall commands, Lynis installation and audit execution, package management activities, and system processes. These records demonstrated how security-relevant actions are logged and can be traced through the system audit trail.
### Security Relevance
Authentication logs provide visibility into user activity and privileged operations. Security analysts use these logs to investigate incidents, verify administrative actions, monitor privileged access, and establish timelines during forensic investigations.
## Phase 6: Firewall Hardening
### Objective
The objective of this phase was to configure and enable the Ubuntu Uncomplicated Firewall (UFW) to reduce the system's attack surface and improve network security.
### Commands Used
- sudo ufw status verbose
- sudo ufw enable
- sudo ufw default deny incoming
- sudo ufw default allow outgoing
- sudo ufw status numbered
### Findings
The firewall was enabled successfully using UFW. The default policy was configured to deny all incoming connections while allowing outgoing traffic. Verification of the firewall status confirmed that UFW was active and enforcing the configured rules.
### Security Relevance
A firewall acts as a security barrier between a system and external networks. Restricting incoming connections helps reduce the attack surface and prevents unauthorized access to services running on the system. Firewall configuration is a fundamental security control used in system hardening.
## Phase 7: File Permissions and User Access Review
### Objective
The objective of this phase was to review file permissions, verify user privileges, and examine local user account information to better understand access control on the system.
### Commands Used
- ls -l
- chmod 600 security-test.txt
- whoami
- getent group sudo
- cat /etc/passwd
### Findings
A test file was created and its permissions were modified from the default settings to a more restrictive configuration using chmod 600. User account information was reviewed to identify the current logged-in user and verify sudo group membership. The /etc/passwd file was examined to review local user accounts and system service accounts configured on the machine.
### Security Relevance
File permissions and user privileges are fundamental security controls in Linux systems. Restricting access to files helps protect sensitive data, while reviewing user accounts and administrative privileges helps ensure that access is granted only to authorized users. Regular permission and account reviews support the principle of least privilege and strengthen system security.
## Phase 8: Service Review and Hardening
### Objective
The objective of this phase was to identify and review active services running on the Ubuntu system to understand which services were exposed and could potentially increase the attack surface.
### Commands Used
systemctl list-units --type=service --state=running
### Findings
A total of 32 running services were identified using the systemctl command. Core services included NetworkManager, cron, dbus, gdm, systemd-resolved, rsyslog, and other system-related services required for normal operating system functionality. This review provided visibility into which services were active and available on the host.
### Security Relevance
Reviewing active services helps security analysts identify unnecessary or potentially risky services that may increase the attack surface. Understanding which services are running is an important step in system hardening and can help reduce exposure to vulnerabilities by disabling services that are not required.
## Phase 9: Malware and Rootkit Detection
### Objective
The objective of this phase was to perform malware and rootkit detection on the Ubuntu system to identify potential security threats, hidden processes, or indicators of compromise.
### Commands Used
- rkhunter --check
- chkrootkit
### Findings
Rootkit and malware detection scans were performed using Rkhunter and Chkrootkit. The tools reviewed system files, running processes, network interfaces, and common rootkit signatures. Rkhunter generated warnings related to possible packet-sniffing activity and a potential BPFDoor malware indicator, while Chkrootkit reported several entries that required further investigation. No confirmed malware infections or active rootkits were identified during the assessment.
### Security Relevance
Malware and rootkit detection are important components of endpoint security monitoring. Regular scanning helps identify hidden threats, unauthorized modifications, and suspicious system activity that may not be visible through standard monitoring techniques. These checks support early threat detection and strengthen overall system security.
## Phase 10: System Updates and Patch Management
### Objective
The objective of this phase was to update installed packages and apply available security patches to reduce known vulnerabilities and improve the overall security posture of the system.
### Commands Used
- sudo apt update
- sudo apt upgrade
### Findings
System packages were reviewed and updated using the Ubuntu package manager. Multiple packages were upgraded to newer versions, ensuring that the operating system contained the latest security fixes and software improvements available at the time of the assessment.
### Security Relevance
Regular patch management is a fundamental security practice. Keeping systems updated helps protect against known vulnerabilities, reduces the risk of exploitation, and ensures that security controls operate with the latest fixes and improvements.
## Phase 11: Final Security Audit and Validation
### Objective
The objective of this phase was to perform a final security assessment after implementing security controls and remediation measures to validate the effectiveness of the hardening process.
### Commands Used
sudo lynis audit system
### Findings
A final Lynis security audit was conducted to evaluate the system after completing the hardening activities. The audit reported a hardening index score of 68 and confirmed that security controls such as firewall configuration, malware scanning, service review, permission checks, and system updates had been completed. The results provided an updated view of the system's security posture following remediation efforts.
Initial Lynis Hardening Index: 67
Final Lynis Hardening Index: 68
### Security Relevance
Performing a final validation audit helps verify that security improvements have been successfully implemented and that the system's overall security posture has improved. Reassessment is an important step in security hardening because it provides measurable evidence of remediation efforts and identifies any remaining areas for improvement.
