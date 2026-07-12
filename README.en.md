# SUMA Cloud-HFS

### Cloud HTTP File Sharing / Cloud-based HTTP File Sharing Tool

SUMA Cloud-HFS (Cloud HTTP File Sharing) is a free, no-account-required Windows desktop file sharing service. It lets you share files over your local network, or create temporary remote download links via Cloudflare Tunnel. Developed by [LOCALSOFT Digital Studio](https://suma.tw).

Through Cloudflare's remote secure tunnel (reverse proxy), **no account registration and no Cloudflare account needed** to create a temporary public download link, enabling remote users on different networks to directly download files from your computer. This technology perfectly bypasses firewalls and broadband internal networks (NAT/CGNAT), requires no static public IP and no port forwarding configuration.

---

## Quick Start

1. Launch Cloud-HFS.
2. Add folders or files in the "Share Management" panel.
3. Return to the dashboard and start the sharing service.
4. Share the displayed URL or QR Code with the recipient.

*For cross-network sharing, enable "Cloudflare Sharing" and start remote sharing.*

> 💡 **Linux CLI Server Version**: If you are running on a Linux server, NAS, or headless environment, please refer to the [Linux CLI Installation and Usage Guide](INSTALL_Cloud-HFS_LINUX_CLI.en.md).

---

## Overview

Cloud-HFS provides a graphical interface to manage HTTP file sharing services. You can configure the site name, port, HTTP sharing service logo, download speed limits, and resumable downloads, as well as import and export settings and share items. The sidebar displays real-time connection counts and download traffic, giving you a clear view of sharing status.

**Web-First Cross-Platform Architecture Refactor:**
This refactor makes the web interface the core experience, focuses the desktop shell on system integration and native capabilities, and accounts for Windows, Linux, and macOS differences to create a stronger base for future cross-platform development and expansion.

---

## Features

### 📂 Share Management
- Windows desktop graphical interface.
- Share entire folders, specific files, or URLs, with multi-select batch add support.
- Multi-level virtual directory management for flexible sharing structure.
- Supports import and export of settings and share items.

### 🌐 Remote Sharing
- Displays LAN access URL and QR Code.
- Service binds to LAN IP by default, with Windows offline environment fallback detection.
- Create temporary remote sharing URLs via Cloudflare Tunnel (**free, no registration, no Cloudflare account needed**).
- On-demand short URL generation (`suma.tw`).

### 📥 Download Experience
- Supports download speed limits (global / per-user dynamic allocation) and HTTP Range resumable downloads.
- Download password protection to secure shared content.
- Customizable HTTP sharing service logo on download page.
- Responsive download page for desktop, tablet, and mobile.
- "Back to top" floating button on download page for long list navigation.

### ⚙️ System and Settings
- Sidebar displays real-time connection count and download traffic.
- Records download count, traffic, and download history.
- Supports Traditional Chinese, Simplified Chinese, and English interface; auto-detects system language on first launch.
- Automatic update check on startup: daily, weekly, or monthly frequency.

### 💻 Web-First Cross-Platform Architecture
- Protects system and sensitive paths according to Windows, Linux, and macOS rules when adding shares, reducing accidental exposure.
- Strengthens Tauri Mock testing and API behavior handling for more reliable cross-platform feature validation.
- Aligns desktop window initialization and native error handling for more consistent application integration across platforms.

---

## Beta Test Version

Beta test versions may have a usage expiry date. This is not a paywall — the purpose is to keep testers on a recent version so they can report issues and help improve stability, security, and overall experience. When the expiry approaches, the program preserves the ability to export settings, so users can save their configuration before updating to the latest version.

---

## Version Check

Go to "Basic Settings" > "Check for Updates" and choose daily, weekly, or monthly. The default is weekly. The program checks the official SUMA version list on startup according to your frequency; when a new version is found, it shows the update details and a download button.

After changing and saving the check frequency, Cloud-HFS immediately runs a version check. A failed check does not affect file sharing services.

---

## License and Terms of Use

Detailed license and copyright information has been moved to:
* [LICENSE_zh-TW.md](LICENSE_zh-TW.md) (繁體中文)
* [LICENSE_zh-CN.md](LICENSE_zh-CN.md) (简体中文)
* [LICENSE_en.md](LICENSE_en.md) (English)

---

## About the Author

- **Author:** LOCALSOFT Digital Studio
- **Website:** [https://suma.tw](https://suma.tw)

---

Copyright 2026 [LOCALSOFT Digital Studio](https://suma.tw). All rights reserved.
