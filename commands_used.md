# 🧪 Commands Used – Day #17: Splunk Universal Forwarder Setup

## 🛠️ Step 1: Install Splunk Universal Forwarder

```bash
wget -O splunkforwarder-ubuntu.deb https://download.splunk.com/products/universalforwarder/releases/latest/linux/splunkforwarder-latest-linux-2.0-amd64.deb
sudo dpkg -i splunkforwarder-ubuntu.deb
cd /opt/splunkforwarder/bin
sudo ./splunk enable boot-start --accept-license
```
### 🔗 Step 2: Configure Forwarder to Send Logs

```bash
sudo ./splunk add forward-server <splunk-server-ip>:9089
```
### 📝 Step 3: Monitor Syslog Files
```bash
sudo ./splunk add monitor /var/log/syslog -index main -sourcetype syslog
sudo ./splunk add monitor /var/log/auth.log -index main -sourcetype authlog
sudo ./splunk restart
```

### 📡 Step 4: Enable Listening on Splunk Indexer
On the Splunk Server:
```bash
sudo /opt/splunk/bin/splunk enable listen 9089
sudo /opt/splunk/bin/splunk list forward-server
```
### 🔍 Step 5: Verify in Splunk Web
Use this search in Search & Reporting:

```spl
index=main sourcetype=syslog | table _time host sourcetype message
```
