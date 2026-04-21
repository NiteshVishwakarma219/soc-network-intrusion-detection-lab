🛡️ Network Intrusion Detection Lab using Suricata IDS + Wazuh SIEM
📌 Overview

This project demonstrates a hands-on SOC Home Lab where I implemented a Network Intrusion Detection System (NIDS) using Suricata IDS integrated with Wazuh SIEM.

The goal of this lab is to detect real-time malicious network activities such as port scanning and suspicious traffic and analyze them in a centralized SIEM dashboard.

🏗️ Lab Architecture
Attacker Machine (Kali Linux)
        |
        |  Nmap / Attack Traffic
        ↓
Victim Machine (Ubuntu)
Suricata IDS (Packet Detection)
        ↓
Log Generation (fast.log / eve.json)
        ↓
Wazuh Agent
        ↓
Wazuh Manager + Dashboard
        ↓
Security Alert Visualization
⚙️ Technologies Used
Suricata IDS (Network Intrusion Detection System)
Wazuh SIEM
Ubuntu Linux (Victim Machine)
Kali Linux (Attacker Machine)
Nmap (Attack Simulation)
Linux Logging System
SOC Monitoring Tools
🔧 Setup & Configuration
1️⃣ Install Suricata IDS
sudo apt update
sudo apt install suricata -y
2️⃣ Verify Installation
which suricata
suricata -V
3️⃣ Start Suricata on Network Interface
ip a
sudo suricata -D -i eth0

(Replace eth0 with correct interface like ens33 or enp0s3)

4️⃣ Monitor Logs
tail -f /var/log/suricata/fast.log
⚔️ Attack Simulation
🔹 Port Scan Attack (Nmap)

From Kali Linux:

nmap -sS <Ubuntu-IP>
📡 Wazuh Integration

Add Suricata log monitoring in Wazuh agent configuration:

<localfile>
  <log_format>syslog</log_format>
  <location>/var/log/suricata/fast.log</location>
</localfile>

Restart Wazuh agent:

sudo systemctl restart wazuh-agent
📊 Detection Results

Wazuh successfully detected and displayed:

Network Port Scanning (Nmap SYN Scan)
Suspicious network activity logs
Suricata IDS alerts in SIEM dashboard
🧠 Key Skills Demonstrated
Network Intrusion Detection (NIDS)
Security Information and Event Management (SIEM)
Traffic Analysis & Packet Inspection
SOC Alert Investigation
Linux Security Monitoring
Detection Engineering Fundamentals
🧪 SOC Use Case

This lab simulates a real-world SOC scenario where:

Attacker performs reconnaissance using Nmap
IDS detects malicious network behavior
SIEM correlates and visualizes security events
Analyst investigates alerts in dashboard
📸 Screenshots

Add your screenshots here:

/screenshots/wazuh-alert.png
/screenshots/nmap-scan.png

🚀 Future Improvements
Add pfSense firewall integration
Enable Suricata EVE JSON advanced logging
Automate threat blocking (Active Response)
Add MITRE ATT&CK mapping
Integrate threat intelligence feeds

👨‍💻 Author
Nitesh Vishwakarma


⭐ Project Outcome

This project strengthens my understanding of Blue Team operations, intrusion detection systems, and SOC workflows using real-world tools like Suricata and Wazuh.
