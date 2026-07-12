# SUMA Cloud-HFS (Linux CLI 版本下载与使用说明)

### Cloud HTTP File Sharing / 云端 HTTP 文件分享工具

本指南将引导您如何在 Linux 服务器、NAS 或无头（Headless）环境中下载、部署与使用 **SUMA Cloud-HFS Linux CLI 版本 (cloud-hfs-daemon)**。

---

## 📥 下载 Linux CLI 可执行文件

目前提供测试版本的 GitHub Release 下载链接（以最新的测试版本为例）：

- **Linux x86_64 (64位) 测试版本下载：**
  [https://github.com/localsoft-suma/SUMA-Cloud-HFS/releases/download/test-release/cloud-hfs-daemon](https://github.com/localsoft-suma/SUMA-Cloud-HFS/releases/download/test-release/cloud-hfs-daemon)

您可以直接在 Linux 终端中使用 `wget` 或 `curl` 命令进行下载：

```bash
# 使用 wget 下载
wget https://github.com/localsoft-suma/SUMA-Cloud-HFS/releases/download/test-release/cloud-hfs-daemon

# 或使用 curl 下载
curl -L -O https://github.com/localsoft-suma/SUMA-Cloud-HFS/releases/download/test-release/cloud-hfs-daemon
```

---

## 🛠️ 安装与授权

下载完成后，请将可执行文件移动到您想要运行的目录，并赋予执行权限：

```bash
# 赋予执行权限
chmod +x cloud-hfs-daemon
```

*（可选）如果您想在任何路径直接执行，可以将其移动至系统环境路径下：*
```bash
sudo mv cloud-hfs-daemon /usr/local/bin/
```

---

## 🚀 服务启动与控制

CLI 版本支持以守护进程（Daemon）在后台运行，即使关闭 SSH 连接，分享服务亦不会中断。

### 1. 启动后台服务
```bash
./cloud-hfs-daemon --start
```
*启动后会自动在同目录下生成 `cloud-hfs-daemon.pid` 记录进程编号，且会默认自动开启文件分享服务。*

### 2. 检查运行状态
```bash
./cloud-hfs-daemon --status
```
*如果服务正在运行，将会显示当前的进程 PID、管理界面访问网址。*

### 3. 停止后台服务
```bash
./cloud-hfs-daemon --stop
```
*安全关闭文件分享服务与 Web 管理后台。*

### 4. 在前景直接运行（不脱离终端）
```bash
./cloud-hfs-daemon --serve
```
*若您希望将此服务加入 systemd 等系统服务管理器，可使用此参数进行配置。*

---

## ⚙️ 远程网页管理（Web SPA）

CLI 版本启动后，会在本地建立一个轻量级的网页版管理面板：

- **默认访问网址**：`http://localhost:1666`
- **远程或局域网管理**：请将网址中的 `localhost` 替换为该 Linux 服务器的实际 IP（例如 `http://192.168.1.100:1666`）。
- **默认文件系统浏览起点**：在网页点击新增分享项目时，文件选择器会默认从执行该程序之用户的家目录（`$HOME`）开始浏览。
- **保护敏感路径**：系统会自动防护并阻挡敏感的系统路径（如 `/etc`、`/proc`、根目录 `/` 等），确保服务器数据安全。

> **⚠️ 安全建议：** 首次连接登录后，请务必至「系统设置」页面设置「管理界面密码」，以防止未授权用户访问您的服务器文件管理后台。

---

## 📂 系统设置与日志路径

在 Linux 环境中，系统相关设置与数据库默认存放于用户的 `.config` 目录下：
- **配置文件与数据库目录**：`~/.config/cloud-hfs/`
- **后台服务日志（Log）**：会存放在 `~/.config/cloud-hfs/cloud-hfs-daemon.log`

---

## ☁️ 启用远程穿透分享

如果需要让非局域网的远程用户下载文件，您可以透过内置的 Cloudflare Tunnel 技术进行内网穿透：
1. 使用浏览器登录 Web 管理界面。
2. 切换至 **「Cloudflare 分享」** 页面。
3. 点击 **「启动远程分享」**（首次启用系统会自动安装 `cloudflared` 组件）。
4. 通道建立成功后，即可复制公开的分享网址，或点击取得专属 `suma.tw` 短网址分享给远程亲友。

---

## 关于作者与技术支持

- **开发维护：** 域创数码工作室 (LOCALSOFT Digital Studio)
- **官方网站：** [https://suma.tw](https://suma.tw)
- **问题反馈：** [https://suma.tw/QTn3kk](https://suma.tw/QTn3kk)

---

Copyright 2026 [LOCALSOFT Digital Studio](https://suma.tw). All rights reserved.
