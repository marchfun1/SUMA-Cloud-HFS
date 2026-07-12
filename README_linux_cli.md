# SUMA Cloud-HFS (Linux CLI 版本使用指南)

### Cloud HTTP File Sharing / 雲端 HTTP 檔案分享工具

SUMA Cloud-HFS（Cloud HTTP File Sharing 的縮寫）是免費、免帳號即可使用的 HTTP 檔案分享服務。本 Linux CLI 版本專為伺服器與命令列環境設計，支援在背景以守護行程（Daemon）持續運行，並提供功能完整的網頁版管理介面（Web SPA），方便您從區域網路或遠端瀏覽器進行管理。

本專案由 [域創數位工作室 (LOCALSOFT Digital Studio)](https://suma.tw) 開發維護。

---

## 快速開始

1. 將編譯好的 `cloud-hfs-daemon` 執行檔放置於 Linux 伺服器中。
2. 賦予執行權限：
   ```bash
   chmod +x cloud-hfs-daemon
   ```
3. 啟動背景服務：
   ```bash
   ./cloud-hfs-daemon --start
   ```
4. 服務啟動後，系統會自動在終端機輸出管理介面網址（預設為 `http://localhost:1666`，可使用區網 IP 進行遠端存取）。
5. 使用瀏覽器開啟管理介面，即可開始新增分享目錄、檔案或連結。

---

## 命令列指令說明

執行 `cloud-hfs-daemon` 支援以下指令：

| 指令 | 說明 |
| :--- | :--- |
| `--start` | 在背景啟動檔案分享與管理服務（會自動脫離目前的終端機工作階段）。 |
| `--status` | 檢視當前服務的運作狀態（若在運行中，會顯示進程 PID 以及管理介面存取網址）。 |
| `--stop` | 安全停止背景運行的服務。 |
| `--serve` | 在前景直接運行服務（主要用於系統服務如 systemd 整合，會佔用當前終端機視窗）。 |
| *(無參數)* | 顯示指令用法說明。 |

---

## 功能特色

### 💻 專為 Linux 伺服器優化的 CLI 模式
- **背景安全分離**：使用 `--start` 啟動後，即使關閉 SSH 終端機，服務仍會在背景持續穩定運作。
- **PID 進程管理**：自動在設定目錄下產生 `cloud-hfs-daemon.pid` 檔案以確保進程狀態一致，防止重複啟動。
- **自動啟動分享**：與桌面版不同，Linux CLI 版本啟動時會預設自動開啟檔案分享服務，方便隨開即用。

### 🌐 遠端網頁 SPA 管理介面
- **Web-First SPA 架構**：系統啟動後會建立一個輕量且直覺的網頁管理後台。您可以使用任何裝置（電腦、平板、手機）連線至 `http://<伺服器IP>:1666` 進行設定。
- **完整功能管理**：包含分享目錄/檔案新增與排序、下載記錄統計與 CSV 匯出、日誌檢視、下載速限與密碼保護等。
- **安全防護機制**：
  - 支援設定管理後台密碼。未設定時，首頁與設定頁面會顯示醒目的安全警示。
  - 支援自動 Bearer Token 驗證，並在登入過期時提供無感自動重試。

### 📂 檔案分享與路徑防護
- **虛擬目錄與層級**：支援多層級虛擬目錄管理，讓您可以彈性且乾淨地組織分享結構。
- **路徑防護機制**：在新增本機檔案或資料夾時，系統會自動阻擋常見的敏感與系統路徑（如：`/etc`、`/proc`、根目錄 `/`、`/System/Library`、使用者庫 `~/Library` 等），降低機密資料外洩風險。
- **預設路徑優化**：新增分享項目時，檔案選擇器預設將從使用者家目錄（`$HOME`）開始瀏覽。

### ☁️ 免費 Cloudflare Tunnel 遠端穿透分享
- 不需要公網 IP，也不需要設定 NAT 轉送與連接埠對應。
- **免註冊帳號、免費使用**：在「Cloudflare 分享」設定中一鍵啟動，即可產生一個臨時的公開下載連結。
- 支援一鍵取得專屬 `suma.tw` 短網址，方便與遠端好友分享。

---

## 授權與使用條款

詳細的版權聲明與授權條款請參閱：
* [doc/LICENSE_zh-TW.md](file:///d:/MyProjects/SUMA-Cloud-HFS-Web/doc/LICENSE_zh-TW.md) (繁體中文)
* [doc/LICENSE_zh-CN.md](file:///d:/MyProjects/SUMA-Cloud-HFS-Web/doc/LICENSE_zh-CN.md) (简体中文)
* [doc/LICENSE_en.md](file:///d:/MyProjects/SUMA-Cloud-HFS-Web/doc/LICENSE_en.md) (English)

---

## 關於作者

- **作者：** 域創數位工作室 (LOCALSOFT Digital Studio)
- **網站：** [https://suma.tw](https://suma.tw)

---

Copyright 2026 [LOCALSOFT Digital Studio](https://suma.tw). All rights reserved.
