# 📄 Findings – Day #17: Splunk Universal Forwarder Setup

## ✅ Objective

Successfully configured a **Splunk Universal Forwarder (UF)** on a remote Ubuntu machine to send logs to a centralized Splunk indexer.

---

## 🔍 Key Findings

### 🔗 Forwarding Setup

- UF installed and configured using:
  ```bash
  sudo ./splunk add forward-server <splunk-server-ip>:9089
### 🔗 Connection to Splunk Indexer Verified With:

```bash
sudo /opt/splunk/bin/splunk list forward-server
```

### 📝 Monitored Logs

Enabled monitoring of key log files:

- `/var/log/syslog` – General system activity  
- `/var/log/auth.log` – Authentication-related events

### 📶 Log Reception

Verified ingestion using Splunk Web Search with:

```spl
index=main sourcetype=syslog | table _time host sourcetype message
```

### 📌 Observations

- Forwarded logs began appearing in Splunk within seconds after UF restart.
- Indexed logs included system events and authentication attempts from the remote host.
- Ensured network connectivity on port `9089` between UF and Splunk indexer.

---

### 🧠 Lessons Learned

- The **Universal Forwarder** is lightweight and highly effective for real-time log shipping.
- Proper port access and indexer listener setup (`splunk enable listen`) are critical for success.
- Monitoring system logs with Splunk enables faster detection of security events and anomalies.

### 📸 Evidence

![Successful Syslog Ingestion](images/splunk-syslog-ingestion.png)
