# 🔐 SSH Log Analysis Using Splunk
<p align="center"><img width="638" height="193" alt="image" src="https://github.com/user-attachments/assets/1e866624-c907-4a23-94b1-19717b20a8a5" /></p>

<div align="center">

![Splunk](https://img.shields.io/badge/Splunk-Enterprise-green?style=for-the-badge\&logo=splunk)
![Cybersecurity](https://img.shields.io/badge/Cybersecurity-Log%20Analysis-blue?style=for-the-badge)
![SOC](https://img.shields.io/badge/SOC-Analyst-red?style=for-the-badge)
![Linux](https://img.shields.io/badge/Linux-SSH-orange?style=for-the-badge)

**Detecting Brute-Force Attacks, Unauthorized Access Attempts, and Suspicious SSH Activity Using Splunk Enterprise**

</div>

---

## 📌 Project Overview

This project focuses on analyzing SSH authentication logs using Splunk Enterprise to identify suspicious login activities, detect brute-force attacks, and monitor unauthorized access attempts on Linux systems.

By ingesting and analyzing SSH logs, security analysts can gain visibility into authentication events, investigate anomalies, and create real-time alerts for rapid threat detection.

---

## 🎯 Objectives

* Detect successful SSH login attempts
* Identify failed login attempts
* Detect brute-force attacks through multiple failed authentications
* Monitor suspicious connections without authentication
* Create security dashboards for SSH monitoring
* Configure real-time alerts for threat detection

---

## 🛠️ Technologies Used

| Technology                       | Purpose                   |
| -------------------------------- | ------------------------- |
| Splunk Enterprise                | Log Analysis & Monitoring |
| SPL (Search Processing Language) | Querying & Investigation  |
| Linux (RHEL/Ubuntu/CentOS)       | SSH Log Generation        |
| Universal Forwarder              | Log Collection            |
| JSON Logs                        | Data Source               |

---

## 📂 Dataset Information

The dataset contains SSH authentication logs in JSON format with events such as:

* Successful SSH Login
* Failed SSH Login
* Multiple Failed Authentication Attempts
* Connection Without Authentication

---

## 🔍 Key Use Cases

### 🚨 Failed Login Monitoring

Identify repeated failed login attempts from source IP addresses.

### 🔥 Brute Force Detection

Detect multiple authentication failures indicating password attacks.

### ✅ Successful Login Tracking

Monitor successful logins and their originating IP addresses.

### ⚠️ Unauthorized Access Monitoring

Detect suspicious SSH connections without authentication.

### 📊 Security Visualization

Create dashboards to provide visibility into SSH activity.

---

## 📝 SPL Queries

### Failed Login Attempts

```spl
index=ssh_logs event_type="Failed SSH Login"
| stats count by id.orig_h
```
<img width="1075" height="517" alt="image" src="https://github.com/user-attachments/assets/5480fa3a-e87b-44a0-9551-5bbfb33a5eca" />
<img width="1084" height="533" alt="image" src="https://github.com/user-attachments/assets/e0058787-9624-4d40-8b7e-843b40ce67d0" />

### Brute Force Detection

```spl
index=ssh_logs event_type="Multiple Failed Authentication Attempts"
| stats count by id.orig_h, id.resp_h
```
<img width="1058" height="502" alt="image" src="https://github.com/user-attachments/assets/21fab398-b3c2-4cf0-bfce-f5697288c5fd" />

### Successful Logins

```spl
index=ssh_logs event_type="Successful SSH Login"
| stats count by id.orig_h, id.resp_h
```
<img width="1048" height="474" alt="image" src="https://github.com/user-attachments/assets/18edf598-183e-425a-879f-569f26937758" />

### Connections Without Authentication

```spl
index=ssh_logs event_type="Connection Without Authentication"
| stats count by id.orig_h
```
<img width="1079" height="504" alt="image" src="https://github.com/user-attachments/assets/d6b48c2d-a079-4fb1-bfde-a0c1b4ee20a9" />

### Authentication Activity Timeline

```spl
index=ssh_logs
| timechart count by event_type
```
<img width="1053" height="527" alt="image" src="https://github.com/user-attachments/assets/f8f7ee98-0992-49e3-a021-a7046a90dac6" />

---

## 📊 Dashboard Components

* Failed Login Attempts
* Successful Logins
* Top Source IPs
* Top Target Users
* SSH Activity Timeline
* Brute Force Detection Panel
* Suspicious Connections Panel

---

## 🚨 Alert Configuration

### Brute Force Alert

**Condition:**

* More than 5 login attempts
* Within 10 minutes
* Real-time monitoring enabled

**Action:**

* Trigger Splunk Alert
* Add to Triggered Alerts
* Notify Security Team

---

## 🎯 Key Findings

* Detected multiple brute-force login attempts.
* Identified suspicious source IP addresses.
* Observed successful logins following repeated failures.
* Found unauthorized login attempts using invalid usernames.
* Discovered frequent targeting of privileged accounts such as root and admin.
* Identified unusual login trends and access patterns.
* Improved visibility into SSH authentication activities.

---

## 🛡️ Security Insights

* Repeated failed logins often indicate credential attacks.
* Root accounts remain primary targets for attackers.
* Authentication anomalies can reveal compromised credentials.
* Real-time alerting significantly reduces detection time.
* Continuous monitoring strengthens overall security posture.

---

## 🚀 Future Enhancements

* Integrate Threat Intelligence Feeds
* Add IP Geolocation Analysis
* Correlate SSH Logs with Firewall Logs
* Integrate IDS/IPS Event Correlation
* SOAR-Based Automated Response
* MFA Event Monitoring
* User Behavior Analytics (UBA)
* Risk-Based Alert Prioritization

---

## 📈 Skills Demonstrated

* Splunk Enterprise
* Log Analysis
* Security Monitoring
* Incident Detection
* SPL Querying
* Dashboard Development
* Alert Configuration
* Threat Hunting
* Linux Administration
* SOC Operations

---

## 🏆 Project Outcome

This project demonstrates practical SOC Analyst skills by leveraging Splunk to detect suspicious SSH activity, investigate authentication events, create security dashboards, and implement proactive monitoring through real-time alerts.

---

### 👨‍💻 Author

**Laxmi Dahale**

🔗 Cybersecurity Enthusiast | SOC Analyst Aspirant | Splunk Practitioner

---

⭐ **If you found this project useful, don't forget to star the repository!** ⭐
