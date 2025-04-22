# 🧠 Observation – Day #17: Splunk Universal Forwarder

## 📝 Overview

This task involved installing and configuring the **Splunk Universal Forwarder (UF)** on a remote Ubuntu machine to collect and forward log data to a centralized Splunk server.

## 🔍 Key Takeaways

- **Centralized log collection** significantly improves visibility across systems.
- Using Splunk UF, we were able to forward logs like `/var/log/syslog` and `/var/log/auth.log` in near real-time.
- Connection setup was seamless once the indexer was configured to listen on the correct port (`9089`).
- The process illustrated the importance of **log normalization**, consistent sourcetypes, and correct indexing.

## ⚙️ Technical Observations

- Logs appeared within seconds of restarting the UF service.
- The `splunk list forward-server` command confirmed the forwarder was actively connected.
- The ingestion query:
  ```spl
  index=main sourcetype=syslog | table _time host sourcetype message 
  ```
    allowed for quick validation in Splunk Web.

- Monitoring multiple log paths provided visibility into both system activity and access/authentication patterns.

---

### 🧩 Challenges Faced

- Required ensuring port `9089` was open and not blocked by UFW or firewalls.
- File permission issues could prevent logs from being read by Splunk UF without `sudo`.

---

### ✅ Outcome

Successfully onboarded a remote Linux machine for centralized log monitoring using Splunk.  
This sets the foundation for building alerting rules and dashboards based on live syslog data.
