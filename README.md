# 醫師國考 AI 臨床導師系統

台灣醫師二階國考知識圖譜 + AI 漸進式解析平台

## 功能

- 🗺️ **知識圖譜**：19 大科 + 次專科分類，支援中英文搜尋
- 🤖 **AI 三層解析**：核心觀念 → 臨床推理 → 通則統整 + Mermaid 決策流程圖
- ⭐ **考前複習**：收藏重點題目，分頁瀏覽
- 🔐 **帳號登入**：Email OTP 驗證，管理員可管理白名單
- 🌗 **深色模式**：自動偵測系統偏好，手動切換

## 部署

### 前置需求

- [Supabase](https://supabase.com) 帳號（已建立 `questions`、`allowed_emails`、`admin_users`、`user_progress`、`user_starred` 資料表）
- [Zeabur](https://zeabur.com) 帳號
- GitHub 帳號

### 步驟

1. 將此 repository push 到 GitHub
2. 在 Zeabur Dashboard 建立新專案 → 連接 GitHub repo
3. Zeabur 會自動偵測為靜態網站並部署
4. 設定自訂網域（可選）
5. 到 Supabase → Authentication → URL Configuration，將 **Site URL** 更新為 Zeabur 給的網址

### 檔案結構

```
├── index.html              # 主程式（單檔 SPA）
├── knowledge_graph_data.js # 知識圖譜資料
├── zbpack.json            # Zeabur 部署設定
├── .gitignore
└── README.md
```

## 技術架構

- **前端**：React 18 + Tailwind CSS（Browser Babel 編譯）
- **後端**：Supabase（PostgreSQL + Auth + Storage）
- **知識圖譜引擎**：Python 腳本（`知識圖譜_v3.py`）處理 Obsidian Markdown
