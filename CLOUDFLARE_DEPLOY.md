# Cloudflare Pages 部署指南 🚀

完整的 HotTea Landing Page 部署教學，從 GitHub 連接到上線只需 5 分鐘。

## 📋 目錄

1. [準備工作](#準備工作)
2. [連接 GitHub](#連接-github)
3. [設定部署配置](#設定部署配置)
4. [完成部署](#完成部署)
5. [自訂域名](#自訂域名-可選)
6. [驗證部署](#驗證部署)
7. [常見問題](#常見問題)

---

## 準備工作

### ✅ 檢查清單

- [ ] 擁有 Cloudflare 帳號（[免費註冊](https://dash.cloudflare.com/sign-up)）
- [ ] GitHub 倉庫已推送：`alanhsu0429/HotTeaWeb`
- [ ] 確認所有文件已提交到 `main` 分支

### 📁 專案結構確認

```
HotTeaWeb/
├── index.html         ✅ 主頁
├── privacy.html       ✅ 隱私政策
├── 404.html          ✅ 錯誤頁面
├── HotTea.svg        ✅ Logo
├── HotTea3.png       ✅ 截圖
├── listenweb.png     ✅ 底圖
├── _headers          ✅ Cloudflare 標頭配置
└── robots.txt        ✅ SEO 配置
```

---

## 連接 GitHub

### 步驟 1: 登入 Cloudflare Dashboard

1. 前往 [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. 使用 Google 或 Email 登入

### 步驟 2: 進入 Pages 服務

1. 在左側選單點擊 **「Workers & Pages」**
2. 點擊右上角 **「Create application」** 按鈕
3. 選擇 **「Pages」** 標籤
4. 點擊 **「Connect to Git」**

### 步驟 3: 授權 GitHub

1. 選擇 **「GitHub」**
2. 點擊 **「Connect GitHub」**
3. 在彈出視窗中授權 Cloudflare 訪問你的 GitHub
4. 選擇授權範圍：
   - **推薦**：僅選擇 `HotTeaWeb` 倉庫（更安全）
   - **或**：授權所有倉庫（方便未來部署其他專案）

---

## 設定部署配置

### 步驟 4: 選擇倉庫

1. 在倉庫列表中找到 **`alanhsu0429/HotTeaWeb`**
2. 點擊 **「Begin setup」**

### 步驟 5: 配置建置設定

填寫以下資訊：

#### 基本設定
| 欄位 | 值 | 說明 |
|------|-----|------|
| **Project name** | `hotteaweb` | 將成為你的免費域名前綴 |
| **Production branch** | `main` | 主要部署分支 |

#### 建置設定
| 欄位 | 值 | 說明 |
|------|-----|------|
| **Framework preset** | `None` | 純靜態網站，無需框架 |
| **Build command** | 留空 | 無需建置步驟 |
| **Build output directory** | `/` | 根目錄即為輸出目錄 |

#### 環境變數
| 欄位 | 值 | 說明 |
|------|-----|------|
| **Environment variables** | 無需設定 | 本專案不需要環境變數 |

### 📸 配置截圖參考

```
┌─────────────────────────────────────────┐
│ Set up builds and deployments           │
├─────────────────────────────────────────┤
│ Project name                            │
│ [hotteaweb                         ]    │
│                                          │
│ Production branch                       │
│ [main                              ▼]   │
│                                          │
│ Framework preset                        │
│ [None                              ▼]   │
│                                          │
│ Build command                           │
│ [                                  ]    │
│                                          │
│ Build output directory                  │
│ [/                                 ]    │
└─────────────────────────────────────────┘
```

---

## 完成部署

### 步驟 6: 開始部署

1. 檢查所有設定是否正確
2. 點擊 **「Save and Deploy」** 按鈕
3. Cloudflare 開始自動部署流程

### 步驟 7: 等待部署完成

部署過程約 **1-2 分鐘**，你會看到：

```
✓ Initializing build environment
✓ Cloning repository
✓ Building application
✓ Deploying to Cloudflare's global network
✓ Success! Your site is live
```

### 🎉 部署成功

部署完成後，你會獲得：

- **免費域名**：`https://hotteaweb.pages.dev`
- **HTTPS 自動啟用**：免費 SSL 憑證
- **全球 CDN**：自動分發到全球節點
- **無限流量**：Cloudflare Pages 免費方案無流量限制

---

## 自訂域名（可選）

如果你擁有自己的域名（例如：`hottea.com`），可以進行綁定：

### 步驟 1: 進入自訂域名設定

1. 在專案頁面點擊 **「Custom domains」** 標籤
2. 點擊 **「Set up a custom domain」**

### 步驟 2: 添加域名

1. 輸入你的域名，例如：`hottea.com` 或 `www.hottea.com`
2. 點擊 **「Continue」**

### 步驟 3: 配置 DNS

Cloudflare 會提供兩種方式：

#### 方案 A：域名已在 Cloudflare（推薦）
- 自動配置 DNS，無需手動操作
- 點擊 **「Activate domain」** 即可

#### 方案 B：域名在其他服務商
需要在你的 DNS 服務商添加以下記錄：

```
類型: CNAME
名稱: www (或 @)
值: hotteaweb.pages.dev
TTL: Auto
```

### 步驟 4: 驗證域名

1. DNS 生效時間：5 分鐘 - 24 小時
2. 驗證成功後，Cloudflare 自動核發 SSL 憑證
3. 你的網站將可透過自訂域名訪問

---

## 驗證部署

### ✅ 部署檢查清單

完成部署後，請驗證以下項目：

#### 1. 頁面訪問
- [ ] 訪問 `https://hotteaweb.pages.dev`
- [ ] 主頁正常顯示
- [ ] Logo 和圖片正常載入
- [ ] 字體正確顯示（Noto Sans TC）

#### 2. 導航連結
- [ ] 點擊「隱私權政策」連結
- [ ] 點擊「返回首頁」連結
- [ ] 點擊「立即安裝 Chrome 擴充功能」按鈕

#### 3. 錯誤頁面
- [ ] 訪問不存在的頁面（如：`/test`）
- [ ] 確認 404 頁面正常顯示
- [ ] 404 頁面的返回首頁連結有效

#### 4. 響應式設計
- [ ] 在桌面瀏覽器測試
- [ ] 在手機瀏覽器測試
- [ ] 使用瀏覽器開發者工具測試不同裝置尺寸

#### 5. 性能檢查
- [ ] 開啟瀏覽器開發者工具 (F12)
- [ ] 檢查 Network 標籤，確認：
  - 圖片正確載入
  - 沒有 404 錯誤
  - HTTP 標頭正確設定（可查看 Cache-Control）

### 📊 性能測試工具

使用以下工具測試網站性能：

1. **Google PageSpeed Insights**
   - 網址：https://pagespeed.web.dev/
   - 輸入你的域名進行測試
   - 目標：90+ 分數

2. **GTmetrix**
   - 網址：https://gtmetrix.com/
   - 測試載入速度和優化建議

3. **WebPageTest**
   - 網址：https://www.webpagetest.org/
   - 詳細的性能分析報告

---

## 常見問題

### Q1: 部署後網頁無法顯示？

**可能原因與解決方案：**

1. **DNS 尚未生效**
   - 等待 5-10 分鐘後重試
   - 清除瀏覽器快取

2. **建置設定錯誤**
   - 確認 Build output directory 設為 `/`
   - 確認 Build command 為空

3. **GitHub 權限問題**
   - 重新授權 Cloudflare 訪問 GitHub
   - 確認倉庫為 Public 或已授權

### Q2: 圖片無法顯示？

**檢查項目：**

1. 確認圖片文件已推送到 GitHub
2. 檢查文件名大小寫（Linux 系統區分大小寫）
3. 確認圖片路徑為相對路徑（`HotTea.svg` 而非 `/HotTea.svg`）

### Q3: 更新代碼後網站沒有變化？

**解決步驟：**

1. 確認代碼已推送到 GitHub：`git push origin main`
2. Cloudflare Pages 會自動觸發重新部署
3. 查看部署歷史：Deployments 標籤
4. 清除瀏覽器快取：`Ctrl+Shift+R` (Windows) 或 `Cmd+Shift+R` (Mac)

### Q4: 如何回滾到之前的版本？

**步驟：**

1. 進入專案的 **「Deployments」** 頁面
2. 找到想要回滾的部署版本
3. 點擊該版本右側的 **「...」** 選單
4. 選擇 **「Rollback to this deployment」**
5. 確認回滾操作

### Q5: 如何刪除專案？

**步驟：**

1. 進入專案設定頁面
2. 滾動到最底部
3. 點擊 **「Delete project」**
4. 輸入專案名稱確認刪除

### Q6: 如何設定自動部署？

**預設已啟用：**

- Cloudflare Pages 預設會監聽 GitHub 倉庫
- 每次推送到 `main` 分支時自動觸發部署
- 無需額外設定

**關閉自動部署：**

1. 進入專案設定
2. 找到 **「Builds & deployments」** 區塊
3. 關閉 **「Automatic deployments」**

---

## 進階設定

### 🔧 自訂建置腳本（未來擴展）

如果未來需要添加建置步驟（如圖片壓縮、HTML 壓縮），可以：

1. 創建 `package.json`：
```json
{
  "name": "hotteaweb",
  "version": "1.0.0",
  "scripts": {
    "build": "echo 'No build needed' && exit 0"
  }
}
```

2. 在 Cloudflare Pages 設定中：
   - Build command: `npm run build`
   - Build output directory: `/`

### 📊 添加分析追蹤

**Cloudflare Web Analytics（免費且隱私友善）：**

1. 進入 Cloudflare Dashboard
2. 選擇 **「Web Analytics」**
3. 添加網站並獲取追蹤代碼
4. 將代碼添加到 `index.html` 的 `</head>` 前

```html
<script defer src='https://static.cloudflareinsights.com/beacon.min.js'
        data-cf-beacon='{"token": "YOUR_TOKEN"}'></script>
```

### 🔒 進階安全標頭

如需更嚴格的安全設定，可編輯 `_headers` 文件：

```
/*
  Content-Security-Policy: default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; font-src https://fonts.gstatic.com; img-src 'self' data:; connect-src 'self'
  Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
```

---

## 部署成本

### 💰 Cloudflare Pages 免費方案

| 功能 | 免費方案 | 說明 |
|------|---------|------|
| **每月建置次數** | 500 次 | 對於本專案綽綽有餘 |
| **並行建置** | 1 個 | 一次建置一個 |
| **頻寬** | 無限制 | 完全免費 |
| **請求次數** | 無限制 | 完全免費 |
| **專案數量** | 無限制 | 可部署多個網站 |
| **自訂域名** | 無限制 | 可綁定多個域名 |
| **HTTPS** | 免費 | 自動 SSL 憑證 |
| **全球 CDN** | 包含 | 275+ 個節點 |

---

## 後續維護

### 🔄 更新流程

1. **本地修改代碼**
2. **測試確認無誤**
3. **提交到 Git**：
   ```bash
   git add .
   git commit -m "更新：描述你的變更"
   git push origin main
   ```
4. **自動部署**：Cloudflare 自動檢測並部署
5. **驗證上線**：訪問網站確認變更生效

### 📈 監控與優化

**定期檢查：**
- [ ] 每週檢查部署狀態
- [ ] 每月檢查分析數據
- [ ] 每季進行性能測試
- [ ] 必要時優化圖片和代碼

---

## 聯絡支援

### 🆘 遇到問題？

1. **Cloudflare 官方文件**：https://developers.cloudflare.com/pages/
2. **Cloudflare 社群論壇**：https://community.cloudflare.com/
3. **專案 GitHub Issues**：https://github.com/alanhsu0429/HotTeaWeb/issues

---

## 附錄：指令參考

### Git 常用指令

```bash
# 查看狀態
git status

# 添加所有變更
git add .

# 提交變更
git commit -m "描述訊息"

# 推送到 GitHub
git push origin main

# 查看歷史
git log --oneline -10

# 回滾到特定版本（謹慎使用）
git reset --hard <commit-hash>
```

### 本地測試伺服器

如需在本地預覽網站：

```bash
# 使用 Python 3
python3 -m http.server 8000

# 使用 Python 2
python -m SimpleHTTPServer 8000

# 使用 Node.js (需先安裝 http-server)
npx http-server -p 8000

# 然後訪問：http://localhost:8000
```

---

## ✅ 完成！

恭喜你成功部署 HotTea Landing Page 到 Cloudflare Pages！

你的網站現在：
- ✅ 運行在全球 CDN 上
- ✅ 擁有免費 HTTPS
- ✅ 自動化部署流程
- ✅ 無限流量和請求
- ✅ 99.99% 可用性保證

**下一步建議：**
1. 設定自訂域名（如有）
2. 添加網站分析工具
3. 在社群媒體分享你的網站
4. 持續優化內容和性能

享受你的全球化網站吧！🎉🍵
