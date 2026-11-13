# LLM Dive Hub — 大型語言模型與 AI Agent 互動講義庫

> **國立中正大學 資訊管理研究所 ・ 林坤佑（學號：615530019）**  
> **課程第九週作業：建立一個自己的 AGENTS.md 或 CLAUDE.md**

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live%20Demo-brightgreen?logo=github)](https://yoyo1103.github.io/llm-dive-hub/)
[![Specification](https://img.shields.io/badge/Spec-AGENTS.md-blue)](AGENTS.md)
[![Zero Build](https://img.shields.io/badge/Build-Zero%20Dependency-orange)](#)

---

## 🌟 專案簡介 (Project Overview)

這次作業的核心目標不同於一次性生成的「Vibe Coding」（只求把單一網頁做出來），而是**建立一套可持續擴充的專案規則與數位憲法（AGENTS.md / CLAUDE.md）**，讓任何 AI（或人類開發者）接手時，都能依照同一套視覺規範、檔案架構、互動模板與標準作業程序（SOP），快速且高品質地繼續追加新的教學單元。

本專案參考課堂示範的「[呆一布講義](https://diveai-lab.github.io/diveai-lessons)」，以 **「LLM Dive Hub・現代大型語言模型與 AI Agent 互動講義庫」** 為題，打造一個具備自適應搜尋、分類篩選、純靜態、零建置負擔的現代化互動講義網站。

---

## 🚀 成果線上展示與 Repo 連結

- 🌐 **網頁成果連結 (GitHub Pages)**：`https://<username>.github.io/<repo-name>/`
- 💻 **GitHub Repository 原始碼**：`https://github.com/<username>/<repo-name>`
- 📜 **專案憲法手冊**：參見根目錄 [AGENTS.md](AGENTS.md) 與 [CLAUDE.md](CLAUDE.md)

---

## 📚 已完成之互動講義單元

全站所有單元均為 **自我包含（Self-contained）**，支援雙擊獨立離線預覽，且內建精心設計的原生 JavaScript 互動沙盒：

| 單元編號 | 講義單元名稱 | 核心領域 | 互動體驗沙盒亮點 (Interactive Widget) |
| :--- | :--- | :--- | :--- |
| **Lesson 01** | [直覺理解 Self-Attention 與 Multi-Head 機制](lessons/transformer-attention/index.html) | 基礎架構 | **注意力熱圖與矩陣計算模擬器**：點選句子中任意詞彙，實時觀察 Q×Kᵀ 點積相似度與 Softmax 權重分配。 |
| **Lesson 02** | [現代 RAG 系統架構設計：從 Chunking 到重排序](lessons/rag-system-design/index.html) | 檢索增強 | **RAG 檢索管線策略實驗室**：自由切換切塊大小（128/512/1024 字）、檢索模式（Vector / BM25 / Hybrid）與 Reranker，實時預覽召回精準度。 |
| **Lesson 03** | [AI Agent 核心架構：ReAct 循環與 LLM Wiki 實戰](lessons/llm-agent-patterns/index.html) | Agent 實戰 | **ReAct 自主決策模擬器**：逐步動態演繹 Thought → Action → Observation → Final Answer 決策時間軸。 |

---

## 🛠️ 專案目錄結構

```text
.
├── AGENTS.md                    # [專案憲法] AI 開發與擴充的標準操作準則
├── CLAUDE.md                    # [AI 兼容] 鏡像引導指引
├── README.md                    # [專案說明] 本檔案
├── .nojekyll                    # [部署設定] 確保 GitHub Pages 純靜態相容
├── index.html                   # [全站入口] 即時搜尋、分類篩選、進度指標
├── log.md                       # [決策歷程] Append-only 歷史異動紀錄
├── NOTES.md                     # [現況白板] 當前狀態與下一次接手清單
├── assets/                      # [共用資源]
│   ├── css/
│   │   └── global.css           # 全站共用設計系統、WCAG 色票、排版與陰影
│   ├── js/
│   │   └── main.js              # 首頁即時過濾、計數與互動邏輯
│   └── images/
│       └── logo.svg             # 品牌向量幾何 Logo
└── lessons/                     # [講義內容]
    ├── transformer-attention/   # 單元一
    │   └── index.html
    ├── rag-system-design/       # 單元二
    │   └── index.html
    └── llm-agent-patterns/      # 單元三
        └── index.html
```

---

## 🤖 如果之後要新增頁面，這套規則如何幫助 AI 繼續完成？

這套在 `AGENTS.md` 中定義的體系，透過以下 4 大機制確保任何未來的 AI 都能精準接手：

1. **零摸索的 4 步驟標準擴充 SOP**：
   - AI 接到「新增單元」指令時，不需猜測檔案放哪，依循 `確定 Slug → 複製標準樣板 index.html → 回填首頁 index.html → 登記 log.md & NOTES.md` 即可完成閉環。
2. **拿來即用的 HTML 骨架樣板 (Page Template)**：
   - `AGENTS.md` 第 6 節提供了包含閱讀進度條、麵包屑導航、學習目標 Checkbox、互動沙盒插槽、折疊思考題 `<details>` 與換頁按鈕的完整程式碼，AI 只要填寫內容與專屬 JS 邏輯，不必從零手刻版型。
3. **統一的設計系統（CSS Design System）**：
   - 全站所有按鈕、標籤、卡片、陰影與文字階層皆綁定於 `assets/css/global.css` 的 CSS 變數。AI 新增內容時只要套用標準 class（如 `.lesson-badge`, `.goals-card`, `.callout-tip`, `.quiz-item`），新頁面的質感與色調保證與全站 100% 統一。
4. **歷程追蹤與防呆守則（Quality Guardrails）**：
   - 強制全形標點符號、英文小寫連字號命名、相對路徑防破圖、零打包工具依賴（Zero build steps），杜絕 AI 常見的環境崩潰或路徑失效問題。

---

## 💻 本地預覽方式

本專案為純靜態網站，無需安裝 Node.js 或執行任何 `npm install`：
1. 直接在檔案總管中雙擊 `index.html`，即可在任何瀏覽器中正常瀏覽。
2. 或在專案目錄使用輕量本地伺服器：
   ```bash
   npx serve .
   # 或
   python -m http.server 8000
   ```
