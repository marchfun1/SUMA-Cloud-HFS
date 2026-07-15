# SUMA Cloud-HFS (Linux CLI 版本下載與使用說明)

### Cloud HTTP File Sharing / 雲端 HTTP 檔案分享工具

本指南將引導您如何在 Linux 伺服器、NAS 或無頭（Headless）環境中下載、部署與使用 **SUMA Cloud-HFS Linux CLI 版本 (Cloud-HFS)**。

---

## 📥 下載 Linux CLI 執行檔

目前提供測試版本的 GitHub Release 下載連結（以 0.10.5 版本為例）：

- **Linux x86_64 (64位元) 測試版本下載：**
  [https://github.com/marchfun1/SUMA-Cloud-HFS/releases/download/01005/SUMA-Cloud-HFS_0.10.5.Beta_Linux-CLI_amd64.tar.gz](https://github.com/marchfun1/SUMA-Cloud-HFS/releases/download/01005/SUMA-Cloud-HFS_0.10.5.Beta_Linux-CLI_amd64.tar.gz)

您可以直接在 Linux 終端機中使用 `wget` 或 `curl` 指令進行下載：

```bash
# 使用 wget 下載
wget "https://github.com/marchfun1/SUMA-Cloud-HFS/releases/download/01005/SUMA-Cloud-HFS_0.10.5.Beta_Linux-CLI_amd64.tar.gz"

# 或使用 curl 下載
curl -L -O "https://github.com/marchfun1/SUMA-Cloud-HFS/releases/download/01005/SUMA-Cloud-HFS_0.10.5.Beta_Linux-CLI_amd64.tar.gz"
```

---

## 🛠️ 安裝與授權

下載完成後，請先將壓縮檔解壓縮至家目錄；執行檔會位於 `~/cloud-hfs/`。

```bash
# 解壓縮 tar.gz 至家目錄 (以 0.10.5 版本為例)
tar -zxvf "SUMA-Cloud-HFS_0.10.5.Beta_Linux-CLI_amd64.tar.gz" -C ~

# 賦予執行權限
chmod +x ~/cloud-hfs/Cloud-HFS
```

*（可選）如果您想在任何路徑直接執行，可以將其移動至系統環境路徑下：*
```bash
sudo ln -s ~/cloud-hfs/Cloud-HFS /usr/local/bin/Cloud-HFS
```

---

## 🚀 服務啟動與控制

CLI 版本支援以守護行程（Daemon）在背景運行，即使關閉 SSH 連線，分享服務亦不會中斷。

### 1. 啟動背景服務
```bash
~/cloud-hfs/Cloud-HFS --start
```
*啟動後會自動在同目錄下產生 `Cloud-HFS.pid` 記錄進程編號，且會預設自動開啟檔案分享服務。*

### 2. 檢查運作狀態
```bash
~/cloud-hfs/Cloud-HFS --status
```
*如果服務正在運行，將會顯示當前的進程 PID、管理介面存取網址。*

### 3. 停止背景服務
```bash
~/cloud-hfs/Cloud-HFS --stop
```
*安全關閉檔案分享服務與 Web 管理後台。*

### 4. 在前景直接運行（不脫離終端機）
```bash
~/cloud-hfs/Cloud-HFS --serve
```
*若您希望將此服務加入 systemd 等系統服務管理器，可使用此參數進行配置。*

---

## ⚙️ 遠端網頁管理（Web SPA）

CLI 版本啟動後，會在本機建立一個輕量級的網頁版管理面板：

- **預設存取網址**：`http://localhost:1666`
- **遠端或區網管理**：請將網址中的 `localhost` 替換為該 Linux 伺服器的實際 IP（例如 `http://192.168.1.100:1666`）。
- **預設檔案系統瀏覽起點**：在網頁點選新增分享項目時，檔案選擇器會預設從執行該程式之使用者的家目錄（`$HOME`）開始瀏覽。
- **保護敏感路徑**：系統會自動防護並阻擋敏感的系統路徑（如 `/etc` / `/proc` / 根目錄 `/` 等），確保伺服器資料安全。

> **⚠️ 安全建議：** 首次連線登入後，請務必至「系統設定」頁面設定「管理介面密碼」，以防止未授權用戶存取您的伺服器檔案管理後台。

---

## 📂 系統設定與日誌路徑

在 Linux 環境中，系統相關設定與資料庫預設存放於使用者的 `.config` 目錄下：
- **設定檔與資料庫目錄**：`~/.config/cloud-hfs/`
- **背景服務日誌（Log）**：會存放在 `~/.config/cloud-hfs/Cloud-HFS.log`

---

## ☁️ 啟用遠端穿透分享

如果需要讓非區域網路的遠端用戶下載檔案，您可以透過內建的 Cloudflare Tunnel 技術進行內網穿透：
1. 使用瀏覽器登入 Web 管理介面。
2. 切換至 **「Cloudflare 分享」** 頁面。
3. 點選 **「啟動遠端分享」**（首次啟用系統會自動安裝 `cloudflared` 元件）。
4. 通道建立成功後，即可複製公開的分享網址，或點選取得專屬 `suma.tw` 短網址分享給遠端親友。

---

## 關於作者與技術支援

- **開發維護：** 域創數位工作室 (LOCALSOFT Digital Studio)
- **官方網站：** [https://suma.tw](https://suma.tw)
- **問題回報：** [https://suma.tw/QTn3kk](https://suma.tw/QTn3kk)

---

Copyright 2026 [LOCALSOFT Digital Studio](https://suma.tw). All rights reserved.
