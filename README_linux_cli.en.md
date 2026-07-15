# SUMA Cloud-HFS (Linux CLI Version Download & Usage Guide)

### Cloud HTTP File Sharing / Cloud HTTP File Sharing Tool

This guide will walk you through downloading, deploying, and using **SUMA Cloud-HFS Linux CLI Version (Cloud-HFS)** on Linux servers, NAS, or headless environments.

---

## 📥 Download Linux CLI Binary

The GitHub Release download links are currently available (using version 0.10.5 as an example):

- **Linux x86_64 (64-bit) Test Version Download:**
  [https://github.com/marchfun1/SUMA-Cloud-HFS/releases/download/01005/SUMA-Cloud-HFS_0.10.5.Beta_Linux-CLI_amd64.tar.gz](https://github.com/marchfun1/SUMA-Cloud-HFS/releases/download/01005/SUMA-Cloud-HFS_0.10.5.Beta_Linux-CLI_amd64.tar.gz)

You can download it directly in your Linux terminal using `wget` or `curl` commands:

```bash
# Download using wget
wget "https://github.com/marchfun1/SUMA-Cloud-HFS/releases/download/01005/SUMA-Cloud-HFS_0.10.5.Beta_Linux-CLI_amd64.tar.gz"

# Or download using curl
curl -L -O "https://github.com/marchfun1/SUMA-Cloud-HFS/releases/download/01005/SUMA-Cloud-HFS_0.10.5.Beta_Linux-CLI_amd64.tar.gz"
```

---

## 🛠️ Installation & Permissions

Once downloaded, extract the archive to the `suma-cloud-hfs` directory in your home folder and grant execution permissions:

```bash
# Extract the tar.gz file to ~/suma-cloud-hfs (using version 0.10.5 as an example)
mkdir -p ~/suma-cloud-hfs
tar -zxvf "SUMA-Cloud-HFS_0.10.5.Beta_Linux-CLI_amd64.tar.gz" -C ~/suma-cloud-hfs

# Grant execution permissions
chmod +x ~/suma-cloud-hfs/Cloud-HFS
```

*(Optional) If you want to execute it from any path, you can move it to the system environment path:*
```bash
sudo ln -s ~/suma-cloud-hfs/Cloud-HFS /usr/local/bin/Cloud-HFS
```

---

## 🚀 Service Startup & Control

The CLI version supports running in the background as a daemon, so the file-sharing service will not be interrupted even if you close the SSH connection.

### 1. Start the Background Service
```bash
~/suma-cloud-hfs/Cloud-HFS --start
```
*After starting, it will automatically generate `Cloud-HFS.pid` in the same directory to record the process ID and auto-start the file-sharing service by default.*

### 2. Check Service Status
```bash
~/suma-cloud-hfs/Cloud-HFS --status
```
*If the service is running, it will show the current process PID and the admin web portal URL.*

### 3. Stop the Background Service
```bash
~/suma-cloud-hfs/Cloud-HFS --stop
```
*Safely stops the file-sharing service and the Web administration panel.*

### 4. Run in the Foreground (Interactive Mode)
```bash
~/suma-cloud-hfs/Cloud-HFS --serve
```
*If you want to integrate this service with system service managers like systemd, you can use this parameter.*

---

## ⚙️ Remote Web Management (Web SPA)

After the CLI version is started, it will set up a lightweight web-based admin panel:

- **Default URL**: `http://localhost:1666`
- **Remote or LAN Administration**: Replace `localhost` in the URL with the actual IP address of the Linux server (e.g., `http://192.168.1.100:1666`).
- **Default File System Starting Path**: When adding shared items in the web panel, the file browser will start from the home directory (`$HOME`) of the user running the daemon.
- **Sensitive Path Protection**: The system automatically protects and blocks sensitive system paths (such as `/etc`, `/proc`, root `/`, etc.) to ensure server data safety.

> **⚠️ Security Recommendation:** After logging in for the first time, make sure to set the "Admin Password" in the "Settings" page to prevent unauthorized access to your file administration back-office.

---

## 📂 System Settings & Log Paths

On Linux, system configurations and database are stored in the user's `.config` directory by default:
- **Settings & DB Directory**: `~/.config/cloud-hfs/`
- **Background Service Log (Log)**: Stored in `~/.config/cloud-hfs/Cloud-HFS.log`

---

## ☁️ Enable Cloudflare Tunnel Remote Sharing

If you need to share files with users outside your local area network (LAN), you can use the built-in Cloudflare Tunnel for intranet penetration:
1. Log in to the Web admin interface using your browser.
2. Go to the **"Cloudflare Tunnel"** page.
3. Click **"Start Remote Sharing"** (the system will automatically download and install the `cloudflared` component on the first run).
4. After the tunnel is successfully established, copy the public URL, or click to get a dedicated `suma.tw` short URL to share with your friends.

---

## About Author & Support

- **Developer:** [LOCALSOFT Digital Studio](https://suma.tw)
- **Website:** [https://suma.tw](https://suma.tw)
- **Feedback:** [https://suma.tw/QTn3kk](https://suma.tw/QTn3kk)

---

Copyright 2026 [LOCALSOFT Digital Studio](https://suma.tw). All rights reserved.
