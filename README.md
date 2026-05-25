# Home-lab-for-SOC-Analyst
SOC practice environment using AWS EC2, Kali Linux and Splunk Enterprise

# AWS SOC Lab – Design and Implementation using AWS EC2

## Overview
This project demonstrates the design and implementation of a cloud-based Security Operations Center (SOC) lab using Amazon Web Services (AWS). The lab simulates a real-world SOC environment for monitoring, collecting, analyzing, and responding to security events.

The environment was built using AWS EC2 instances, Splunk SIEM, Windows Server Active Directory, and Kali Linux to provide hands-on cybersecurity experience in cloud security monitoring and SOC operations.

---

# Objectives
The main objectives of this project were:

- Design and deploy a SOC lab using cloud infrastructure
- Configure and manage AWS EC2 instances
- Install and configure Splunk SIEM
- Simulate real-time log collection and monitoring
- Gain practical experience in SOC operations and cybersecurity monitoring

---

# Lab Architecture

The SOC lab environment consists of:

## Components
### 1. Splunk Server (EC2 Instance)
Used for:
- Log collection
- Log indexing
- Event analysis
- Dashboard visualization

### 2. Windows Server (EC2 Instance)
Configured as:
- Active Directory Domain Controller
- Log source machine

### 3. Kali Linux Machine
Used for:
- Remote administration
- SSH access
- Security testing
- SOC management tasks

### 4. Splunk Universal Forwarder
Installed on the Windows Server to:
- Collect Windows logs
- Forward logs to Splunk server

---

# Technologies Used

| Technology | Purpose |
|---|---|
| AWS EC2 | Cloud virtual servers |
| Splunk Enterprise | SIEM platform |
| Windows Server | Active Directory & log source |
| Kali Linux | Client machine & management |
| SSH | Remote Linux access |
| RDP (Remmina) | Remote Windows access |
| Splunk Universal Forwarder | Log forwarding |

---

# System Architecture Flow

```text
Windows Server
      ↓
Splunk Universal Forwarder
      ↓
Splunk Server (AWS EC2)
      ↓
Dashboard Visualization & Monitoring
```

---

# AWS EC2 Deployment

## EC2 Instance Creation
The following instances were created:

- SPLUNK_LAB
- AD_SERVER1

### Configuration Steps
- Selected operating systems
- Configured instance types
- Generated key pairs (.pem)
- Configured storage
- Configured inbound security rules

### Important Ports

| Port | Purpose |
|---|---|
| 22 | SSH |
| 3389 | RDP |
| 8000 | Splunk Web Interface |
| 9997 | Splunk Log Forwarding |

---

# Splunk Installation

## Download Splunk
Splunk was downloaded using `wget` from the official Splunk website.

Example:
```bash
wget <splunk_download_link>
```

## Verify Download
```bash
file splunk-package.tgz
```

## Extract Splunk
```bash
tar -xvzf splunk-package.tgz
```

## Move Splunk Directory
```bash
sudo mv splunk /opt/
```

## Start Splunk
```bash
sudo /opt/splunk/bin/splunk start --accept-license --answer-yes --no-prompt --seed-passwd admin123 --run-as-root
```

## Enable Boot Start
```bash
sudo /opt/splunk/bin/splunk enable boot-start
```

---

# Accessing Splunk Web Interface

Open browser:
```text
http://<Public-IP>:8000
```

Ensure AWS Security Groups allow:
- TCP Port 8000

---

# Active Directory Configuration

Windows Server was configured with:
- Active Directory Domain Services
- AD Lightweight Directory Services

The server was promoted to:
- Domain Controller

This allowed:
- User creation
- Group management
- Security event generation

---

# Splunk Universal Forwarder Configuration

The Universal Forwarder was installed on the Windows Server.

## Configuration Included
- Splunk server IP configuration
- Port 9997 configuration
- Selection of relevant log sources

## Receiving Configuration in Splunk
Splunk receiving port:
```text
9997
```

Was configured under:
```text
Settings → Forwarding and Receiving
```

---

# Log Monitoring

The following logs were monitored:
- User activity logs
- Windows event logs
- Authentication events
- System activity logs

Splunk dashboards were used to:
- Visualize logs
- Monitor events in real time
- Analyze suspicious activities

---

# Results

The SOC lab was successfully implemented.

## Achievements
- Successful cloud SOC deployment
- Real-time log forwarding
- Splunk dashboard visualization
- Monitoring of Windows activities and events

---

# Challenges Faced

## Problems
- AWS Security Group misconfigurations
- Splunk web interface access issues
- Log forwarding problems
- Splunk installation errors

## Solutions
- Updated inbound rules (8000 & 9997)
- Verified IP configurations
- Restarted Splunk services
- Reconfigured forwarder settings

---

# Skills Gained

This project provided practical experience in:

- SOC Operations
- SIEM Configuration
- Log Analysis
- Cloud Security
- AWS EC2 Administration
- Threat Monitoring
- Incident Detection
- Windows Server Administration

---

# Future Improvements

Possible future upgrades:
- Wazuh SIEM integration
- Suricata IDS deployment
- Threat hunting automation
- Security alerting system
- Active Directory attack simulations
- Malware analysis environment

---

# Disclaimer
This project was created strictly for educational and ethical cybersecurity learning purposes only.

---

# Author

## Phares Daniel
Aspiring SOC Analyst | Cybersecurity Enthusiast | Cloud Security Learner

GitHub: https://github.com/YOUR_USERNAME
