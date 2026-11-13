# AGENTS.md — LLM Dive Hub 互動講義專案開發指引

> **專案憲法（Constitution）**：本文件是「LLM Dive Hub（大型語言模型與 AI Agent 互動講義庫）」的最高指導原則。
> 任何接手此專案的 AI Agent（包括 Antigravity、Claude Code、Codex、GitHub Copilot 等）與人類協作者，在新增、修改、維護頁面時，**必須嚴格遵循本文件的規範與工作流程**。
> 本專案的宗旨不是一次性的「Vibe Coding」，而是建立一套**具備高延展性、標準化、可重複依循的互動知識庫系統**。

---

## 1. 專案願景與核心定位

### 1.1 專案目的
「LLM Dive Hub」是一個專為人工智慧自學者、資訊管理與電腦科學領域學生打造的**現代化互動式教學講義平台**。
- **拒絕無聊的靜態閱讀**：每份講義均內建「互動式參數沙盒（Interactive Widgets）」，讓學習者透過直覺操作理解複雜的 AI 機制（如注意力計算、向量檢索、Agent 決策迴圈）。
- **結構化與可擴展**：透過統一的樣板與 SOP，讓無論是人類或 AI，都能在 5 分鐘內無縫追加全新的講義單元，並自動整合入全站索引。
- **純靜態、零建置負擔**：全站採用原生純 HTML5、現代 CSS3、Vanilla JavaScript 開發，無需複雜的 Node.js 構建流程，完美支援 GitHub Pages 隨推即播。

---

## 2. 目錄架構與檔案權限

全站嚴格採用以下樹狀目錄劃分，禁止隨意建立未定義之根目錄：

```text
.
├── AGENTS.md                    # [專案憲法] 本手冊，AI 開發行為的唯一準則
├── CLAUDE.md                    # [AI 兼容] 指向 AGENTS.md 的快速鏡像指引
├── README.md                    # [公開展示] 專案介紹、線上網址、特色說明
├── .nojekyll                    # [部署設定] 確保 GitHub Pages 不受 Jekyll 引擎干擾
├── index.html                   # [全站入口] 講義庫入口首頁：含即時搜尋、分類篩選、進度指標
├── log.md                       # [決策紀錄] 歷次新增講義與系統改版之歷史（Append-only）
├── NOTES.md                     # [現況白板] 目前已完成單元、下次起點、待辦事項（隨時更新）
├── assets/                      # [共用資源] 全站共用資產
│   ├── css/
│   │   └── global.css           # 全站共用 CSS 變數、字體、基礎排版、色彩系統
│   ├── js/
│   │   └── main.js              # 首頁互動邏輯（分類切換、搜尋過濾、卡片計數）
│   └── images/
│       └── logo.svg             # 品牌識別向量 Logo
└── lessons/                     # [講義內容本體] 每個單元獨立一資料夾
    ├── transformer-attention/   # 單元一：直覺理解 Self-Attention 與 Multi-Head 機制
    │   └── index.html           # 該單元之自我包含（Self-contained）頁面
    ├── rag-system-design/       # 單元二：現代 RAG 系統設計（檢索、混合排序）
    │   └── index.html           # 該單元之自我包含頁面
    └── llm-agent-patterns/      # 單元三：AI Agent 核心模式與 Karpathy LLM Wiki 實戰
        └── index.html           # 該單元之自我包含頁面
```

### 檔案權限與防呆規則：
1. **一律英文小寫連字號（kebab-case）**：
   - 講義資料夾名稱必須為 `lessons/<slug>/`，如 `rag-system-design`。嚴禁中文或含有空格的檔案路徑，以確保 GitHub Pages URL 潔淨與跨平台無相容問題。
2. **單一頁面自我包含（Self-contained）**：
   - 每個講義頁面必須命名為 `index.html`。
   - 頁面可獨立在瀏覽器中開啟（雙擊即看），引用全站共用 `assets/css/global.css`，並可內嵌該單元專屬的互動腳本與樣式。
3. **首頁連動更新（Sync with Portal）**：
   - 任何人在 `lessons/` 新增單元時，**必須同步**在根目錄 `index.html` 註冊該講義卡片與標籤。
4. **歷程紀錄三位一體**：
   - 新增或重大修改頁面後，必須更新 `log.md`（永久歷史）與 `NOTES.md`（最新現況）。

---

## 3. 設計系統與視覺規範 (Design System)

本專案採用**現代精緻科技感（Modern Tech-Clean）**，色彩經過嚴謹的 WCAG 2.1 對比度校準，閱讀舒適不疲勞。

### 3.1 核心 CSS 變數定義（定義於 `assets/css/global.css`）
```css
:root {
  /* 品牌核心主色 */
  --primary: #2563EB;          /* 科技湛藍（按鈕、重點強調、高亮連結） */
  --primary-hover: #1D4ED8;    /* 懸浮深藍 */
  --primary-light: #EFF6FF;    /* 湛藍柔光背景 */
  
  /* 輔助漸層色 */
  --accent-purple: #7C3AED;    /* 邏輯/架構紫色 */
  --accent-emerald: #059669;   /* 成功/亮點祖母綠 */
  --accent-amber: #D97706;     /* 提示/思考琥珀黃 */
  
  /* 背景與表面層級 */
  --bg-page: #F8FAFC;          /* 頁面畫布底色（淡藍灰） */
  --bg-card: #FFFFFF;          /* 卡片背景（純白） */
  --bg-subtle: #F1F5F9;        /* 次級區塊/程式碼底色 */
  
  /* 文字層級 (墨水色) */
  --ink-heading: #0F172A;      /* 主標題（深岩藍灰，近黑） */
  --ink-body: #334155;         /* 內文（沉穩鐵灰，最佳閱讀對比） */
  --ink-muted: #64748B;        /* 輔助說明/時間/標籤 */
  --ink-border: #E2E8F0;       /* 邊框線 */
  
  /* 陰影與圓角 */
  --radius-sm: 6px;
  --radius-md: 12px;
  --radius-lg: 20px;
  --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 12px rgba(15, 23, 42, 0.08);
  --shadow-hover: 0 12px 28px rgba(37, 99, 235, 0.12);
  
  /* 字體系 */
  --font-sans: 'Inter', 'Noto Sans TC', system-ui, -apple-system, sans-serif;
  --font-mono: 'JetBrains Mono', Consolas, Monaco, monospace;
}
```

### 3.2 語言與文字排版
- **語系**：頁面一律宣告 `<html lang="zh-Hant">`。
- **標點符號規範**：中文一律使用**全形標點符號**（，。、：！？「」『』），嚴禁混用半形逗號或句號。
- **英文專有名詞保留**：專有名詞保留英文原名（如 *Self-Attention*, *Transformer*, *Embedding*, *Chunking*, *Reranking*, *ReAct Pattern*），避免生硬的過度翻譯。
- **程式碼與公式**：行內程式碼使用反引號包裹；區塊程式碼必須包含語言標註與語法高亮造型。

---

## 4. 單元講義頁面結構（Lesson Architecture）

一份合格的「LLM Dive Hub」講義頁面，必須包含以下**七大標準模組**：

1. **頂部導覽列（Top Bar）**：
   - 品牌標誌與「← 返回講義首頁」麵包屑按鈕。
   - 當前進度條（滾動即時更新讀取百分比）。
2. **單元標頭區（Lesson Hero）**：
   - 分類徽章（如 `基礎架構` / `檢索增強` / `Agent 實戰`）。
   - 主標題（清晰、易懂）與 副標題（一句話說清解決的核心問題）。
   - Meta 資訊：預估閱讀時間（如 `15 分鐘`）、難度等級（`初階` / `進階` / `實戰`）、最後更新日期。
3. **本章學習目標（Learning Objectives）**：
   - 以 Checkbox 造型的 3 個條列項目，清楚告訴學員完成本單元能獲得的具體能力。
4. **核心直覺與理論拆解（Core Intuition & Concepts）**：
   - 拒絕純數學堆砌，必須先給出「生活化比喻」與「為什麼需要這個機制」。
   - 搭配乾淨的架構流程圖或循序圖。
5. **互動實作沙盒（Interactive Sandbox）——核心亮點！**：
   - 每篇講義**必須至少具備一個即時可操作的互動 Widget**（例如：拖拉滑桿觀察 Attention 權重變化、點擊按鈕執行 RAG 步驟模擬、或點選 Agent 決策分支）。
   - 讓讀者動手玩，強化深層記憶。
6. **實用程式碼範例（Code in Action）**：
   - 精簡、可運行的 Python / PyTorch / JavaScript 核心邏輯範例，並附帶關鍵行解說。
7. **隨堂檢測與延伸閱讀（Quiz & Navigation）**：
   - 1~2 題啟發式思考題，使用 HTML `<details><summary>` 標籤，讀者思考後點擊即可展開標準解答。
   - 底部提供「上一單元」與「下一單元」切換連結，形成連貫的學習動線。

---

## 5. AI 新增頁面 4 步驟標準流程 (SOP)

當人類指令要求「*新增一個關於 LoRA 微調的講義單元*」時，AI **必須按部就班執行以下 4 步驟**：

### 步驟 1：確認主題與分配 Slug
- 確定單元分類（`基礎架構` / `檢索增強` / `Agent 實戰` / `模型調優`）。
- 定義英文小寫 slug，例如 `lora-finetuning`。
- 建立資料夾：`lessons/lora-finetuning/`。

### 步驟 2：複製標準樣板並撰寫 `index.html`
- 在 `lessons/lora-finetuning/index.html` 套用第 6 節的標準樣板。
- 依序填入：學習目標、生活比喻、數學/架構拆解、**量身打造的互動 Widget（JavaScript 邏輯）**、範例程式碼、折疊思考題。
- 驗證相對路徑：CSS 引用 `../../assets/css/global.css`，返回連結指向 `../../index.html`。

### 步驟 3：回填首頁 `index.html`
- 在根目錄 `index.html` 的講義列表區塊中，追加一張對應的講義卡片：
  ```html
  <article class="lesson-card" data-category="tuning" data-tags="LoRA PEFT 微調 Fine-Tuning">
    <div class="card-badge badge-amber">模型調優</div>
    <h3 class="card-title">LoRA 參數高效微調直覺拆解</h3>
    <p class="card-desc">不用全量微調數百億參數！透過低秩矩陣分解，只用 0.1% 顯存與參數也能達到滿血效果。</p>
    <div class="card-meta">
      <span>⏱️ 12 分鐘</span>
      <span>⭐ 中階</span>
    </div>
    <a href="lessons/lora-finetuning/index.html" class="card-link">開始學習 →</a>
  </article>
  ```
- 更新首頁上的「講義總數統計計數器」。

### 步驟 4：更新 `log.md` 與 `NOTES.md`
- 在 `log.md` 開頭追加一筆操作紀錄：
  ```markdown
  ## [YYYY-MM-DD] feat | 新增 lessons/lora-finetuning/
  - 主題：LoRA 參數高效微調直覺拆解
  - 互動元件：低秩分解矩陣乘法視覺化模擬器
  - 首頁索引已同步更新
  ```
- 在 `NOTES.md` 中將此項目從待辦清單勾除，並標示目前完成進度。

---

## 6. 標準講義 HTML 骨架樣板 (Page Template)

AI 在新增講義時，請直接以以下標準結構進行擴展填充：

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>單元標題 - LLM Dive Hub</title>
  <link rel="stylesheet" href="../../assets/css/global.css">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=JetBrains+Mono:wght@400;500&family=Noto+Sans+TC:wght@400;500;700;900&display=swap" rel="stylesheet">
  <style>
    /* 單元專屬樣式與互動沙盒外觀 */
    .sandbox-container {
      background: var(--bg-card);
      border: 2px solid var(--ink-border);
      border-radius: var(--radius-md);
      padding: 24px;
      margin: 24px 0;
      box-shadow: var(--shadow-sm);
    }
  </style>
</head>
<body>
  <!-- 頂部閱讀進度指示器 -->
  <div class="reading-progress-bar" id="progressBar"></div>

  <!-- 頂部導覽列 -->
  <header class="top-nav">
    <div class="nav-container">
      <a href="../../index.html" class="back-link">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="m15 18-6-6 6-6"/></svg>
        <span>返回講義庫首頁</span>
      </a>
      <span class="hub-tag">LLM Dive Hub</span>
    </div>
  </header>

  <!-- 主內容容器 -->
  <main class="lesson-wrap">
    <!-- 單元標頭 -->
    <header class="lesson-hero">
      <div class="lesson-badge">核心分類</div>
      <h1 class="lesson-title">單元主標題</h1>
      <p class="lesson-subtitle">這份講義將帶你快速掌握某個關鍵機制，以及它的工程實踐直覺。</p>
      <div class="lesson-meta-bar">
        <span>⏱️ 預估 15 分鐘</span>
        <span>📊 難度：初階</span>
        <span>🔄 2026-11 更新</span>
      </div>
    </header>

    <!-- 學習目標 -->
    <section class="lesson-section goals-card">
      <h2>🎯 本單元學習目標</h2>
      <ul class="goals-list">
        <li>能夠用自己的話說明核心原理與運作直覺。</li>
        <li>掌握關鍵公式背後的幾何與工程意義。</li>
        <li>透過下方互動沙盒，實際觀察不同輸入時的數值動態變化。</li>
      </ul>
    </section>

    <!-- 核心直覺拆解 -->
    <section class="lesson-section">
      <h2>💡 核心直覺與架構</h2>
      <p>詳細教學說明，使用全形標點符號，配合生動的生活實例...</p>
    </section>

    <!-- 互動體驗沙盒 -->
    <section class="lesson-section">
      <h2>🧪 互動體驗沙盒：動手玩看看</h2>
      <div class="sandbox-container">
        <!-- 互動控制項與動態視覺呈現 -->
      </div>
    </section>

    <!-- 程式碼實戰 -->
    <section class="lesson-section">
      <h2>💻 核心實作範例</h2>
      <pre><code># 核心程式碼示範</code></pre>
    </section>

    <!-- 隨堂思考題 -->
    <section class="lesson-section quiz-section">
      <h2>🤔 隨堂思考題</h2>
      <details class="quiz-item">
        <summary>思考題題目：點擊展開解答</summary>
        <div class="quiz-answer">
          <p>這是解答與深入分析...</p>
        </div>
      </details>
    </section>

    <!-- 底部導航 -->
    <nav class="lesson-pagination">
      <a href="#" class="btn-prev">← 上一單元</a>
      <a href="#" class="btn-next">下一單元 →</a>
    </nav>
  </main>

  <footer class="footer">
    <p>© 2026 LLM Dive Hub ・ 開發規範遵循 AGENTS.md</p>
  </footer>

  <script>
    // 閱讀進度條即時更新
    window.addEventListener('scroll', () => {
      const winScroll = document.documentElement.scrollTop;
      const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
      const scrolled = (winScroll / height) * 100;
      document.getElementById('progressBar').style.width = scrolled + '%';
    });
  </script>
</body>
</html>
```

---

## 7. AI 開發遵守的嚴格防呆約束（Quality Guardrails）

1. **嚴禁破壞性覆蓋**：修改既有頁面時，禁止刪除已設計好的互動元件與文字細節，只允許在架構上做正向強化與修補。
2. **純原生無打包依賴**：不可在專案中引入 React/Vue 編譯套件、Webpack 或 Tailwind 建置工具。所有 CSS 與 JS 必須是瀏覽器可直接解析的原生代碼。
3. **字體與 CDN 限制**：只允許引用 Google Fonts 官方字體（Inter, Noto Sans TC, JetBrains Mono）。禁止引用不穩定或需翻牆的未知外部圖檔或 API。
4. **極致響應式適配（RWD）**：所有版面與互動沙盒必須在手機螢幕（375px）、平板（768px）與桌機（1200px）皆能順暢滑動並正常點擊操作。
5. **Git 與 Pages 友善**：專案根目錄必須維持 `.nojekyll`，所有內部超連結一律使用相對路徑（如 `../../index.html`），確保在 GitHub Pages 的二級路徑（`https://username.github.io/repo-name/`）下永遠不會破圖或 404。
