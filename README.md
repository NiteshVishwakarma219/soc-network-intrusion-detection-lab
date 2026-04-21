# 🛡️ SOC Home Lab: Network Intrusion Detection using Suricata IDS + Wazuh SIEM

![Platform](https://img.shields.io/badge/Platform-Ubuntu%20%7C%20Kali-blue)
![Tool](https://img.shields.io/badge/IDS-Suricata-orange)
![Tool](https://img.shields.io/badge/SIEM-Wazuh-purple)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)

---

## 📌 Overview

This project demonstrates a hands-on **Network Intrusion Detection Lab** built using **Suricata IDS integrated with Wazuh SIEM** to detect, forward, and analyze malicious network activity in a SOC-style workflow.

The lab simulates **reconnaissance activity (Nmap SYN Scan)**, validates **Suricata detection**, and ingests alerts into **Wazuh Dashboard** for investigation.

---

## 🎯 Objectives

- Detect suspicious network activity using Suricata IDS  
- Forward IDS alerts into Wazuh SIEM  
- Analyze intrusion events in a centralized dashboard  
- Simulate a real SOC monitoring workflow  
- Practice detection engineering using open-source security tools  

---

## 🏗️ Lab Architecture

```text
Kali Linux (Attacker)
       |
       | Nmap SYN Scan
       v
Ubuntu (Victim)
+------------------+
|  Suricata IDS    |
| Packet Inspection|
+------------------+
       |
       v
Suricata Alerts (fast.log / eve.json)
       |
       v
Wazuh Agent
       |
       v
Wazuh Manager + Dashboard
       |
       v
Security Event Analysis
```

---

## 🛠️ Technologies Used

- Suricata IDS
- Wazuh SIEM
- Ubuntu Linux
- Kali Linux
- Nmap
- Linux CLI
- Security Event Monitoring

---

## ⚙️ Setup

### Install Suricata

```bash
sudo apt update
sudo apt install suricata -y
```

---

### Verify Installation

```bash
which suricata
suricata -V
```

---

### Start Suricata

```bash
ip a
sudo suricata -D -i eth0
```

Replace `eth0` with your actual interface if needed.

---

## 🔗 Wazuh Integration

Configure Wazuh agent to monitor Suricata alerts:

```xml
<localfile>
  <log_format>syslog</log_format>
  <location>/var/log/suricata/fast.log</location>
</localfile>
```

Restart agent:

```bash
sudo systemctl restart wazuh-agent
```

---

## ⚔️ Attack Simulation

### Nmap SYN Scan

Run from Kali:

```bash
nmap -sS <Ubuntu-IP>
```

---

## 🚨 Detection Results

Alerts generated for:

- Port Scanning
- Network Reconnaissance
- Suspicious Traffic Activity

Detected in:

- Suricata Logs
- Wazuh Dashboard

---

## 📊 Sample Alert Workflow

```text
Attack Traffic
   ↓
Suricata Detection
   ↓
Alert Log Generated
   ↓
Wazuh Log Ingestion
   ↓
Dashboard Security Alert
```

---

## 🧠 Skills Demonstrated

- Network Intrusion Detection (NIDS)
- SIEM Log Analysis
- Security Monitoring
- Detection Engineering
- Linux Security Administration
- SOC Investigation Workflow

---

## 📸 Screenshots

Add screenshots here:

```text
screenshots/
├── nmap-attack.png
├── suricata-alert-log.png
└── wazuh-dashboard-alert.png
```

Example:

```md
![Nmap Scan](screenshots/nmap-attack.png)

![Suricata Detection](screenshots/suricata-alert-log.png)

![Wazuh Alert](screenshots/wazuh-dashboard-alert.png)
```

---

## 🧪 MITRE ATT&CK Mapping

| Technique | ID |
|----------|----|
| Network Service Scanning | T1046 |
| Active Scanning | T1595 |

---

## 🚀 Future Improvements

- Add pfSense + Suricata integration
- Enable EVE JSON logging
- Add Active Response blocking
- Add threat intelligence feeds
- Expand into full SOC Home Lab series

---

## 📂 Repository Structure

```text
soc-network-intrusion-detection-lab/
├── README.md
├── screenshots/
   ├── nmap-attack.png
   ├── suricata-alert-log.png
   └── wazuh-dashboard-alert.png

```

---

## 👨‍💻 Author

**Nitesh Vishwakarma**


## ⭐ Project Outcome

Successfully built a functional **Suricata + Wazuh intrusion detection pipeline** and simulated a **real-world SOC detection use case** using open-source security tools.
