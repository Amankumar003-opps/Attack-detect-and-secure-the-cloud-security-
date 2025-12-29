# Attack-detect-and-secure-the-cloud-security-
🛡️ Attack detect and secure the cloud security
Red Team vs Blue Team | SIEM-Driven Security Operations
📌 Project Synopsis

This project represents a full-spectrum cloud security simulation executed on Microsoft Azure, showcasing both offensive (Red Team) and defensive (Blue Team) cybersecurity operations.

A segmented enterprise network was architected, deliberately attacked using real-world techniques, monitored via Wazuh SIEM, and finally secured through hardening and access control enforcement.

🎯 Core Goals

Design a realistic enterprise-grade cloud architecture

Simulate external & internal threat scenarios

Demonstrate post-compromise lateral movement

Detect attacks using SIEM correlation & log analysis

Apply security remediation and infrastructure hardening

🏗️ Cloud Architecture Overview

Platform: Microsoft Azure

🔐 Network Segmentation

DMZ Subnet → Public-facing services

Internal Subnet → Sensitive assets (no public exposure)

🖥️ Deployed Systems
Role	Description
🌐 Web Server (DMZ)	Apache HTTP Server exposed to the internet
📁 Internal File Server	Samba (SMB) server hosting sensitive files
🛡️ SIEM Server	Wazuh Manager + Dashboard
🧨 Attacker	Kali Linux (External Threat Actor)
⚔️ Phase 1: Red Team Operations (Offense)
🔍 Reconnaissance & Enumeration

Tools Used: Nmap, Gobuster

Identified open services (SSH, HTTP)

Enumerated hidden web directories

Fingerprinted outdated Apache components

💥 External Exploitation

Tools Used: Hydra, Nikto

Performed SSH brute-force attacks on Web Server

Generated abnormal authentication failures

Triggered excessive 403/404 responses via web scanning

✔️ Result: Web Server compromised

🚩 Lateral Movement (Pivoting)

Threat Model: Insider / Post-Breach Attack

Used compromised Web Server as a jump box

Scanned internal subnet inaccessible from the internet

Brute-forced internal Samba File Server

✔️ Result: Internal system breached despite isolation

🛡️ Phase 2: Blue Team Operations (Defense)
📊 Detection & Analysis (SIEM)

Using Wazuh Dashboard, the following Indicators of Compromise were identified:

🚨 12,000+ SSH authentication failures

🌐 Detection of Nikto user-agent signatures

🔄 Abnormal internal SSH traffic from private IPs

📈 Sudden spikes in error logs (400-level responses)

🔧 Hardening & Remediation
🔐 SSH Security

Disabled PasswordAuthentication

Disabled PermitRootLogin

Enforced Key-Based Authentication

🌐 Web Server Security

ServerTokens Prod

ServerSignature Off

Reduced attack surface visibility

🧱 Network Security

Restricted NSG rules

Enforced strict east-west traffic controls

Prevented unauthorized lateral access

📉 Post-Hardening Validation

Clean Nmap scans (no version disclosure)

Brute-force attempts blocked

SIEM alert volume normalized

No unauthorized internal access detected

🛠️ Technology Stack

Cloud: Microsoft Azure (VNet, NSG, VMs)
Operating Systems: Ubuntu Linux, Kali Linux
Security & Monitoring: Wazuh SIEM
Attack Tools: Nmap, Hydra, Nikto, Gobuster
Services: Apache HTTP Server, Samba (SMB)

🏁 Final Takeaway

This lab demonstrates how minor misconfigurations can lead to full network compromise, and how visibility + monitoring + segmentation are critical to modern cloud security.

It bridges the gap between attack execution and defensive response, making it a complete SOC-style cloud security project.
