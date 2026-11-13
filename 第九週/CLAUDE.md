# CLAUDE.md — LLM Dive Hub 互動講義專案指引

> 本專案遵循統一的 AI 協作規範。
> 完整的「專案憲法」、設計系統、目錄架構、單元結構規範、AI 擴充 4 步驟 SOP 與標準 HTML 樣板，請全文參閱 **[AGENTS.md](AGENTS.md)**。

---

## 快速摘要 (Executive Summary)

1. **專案目標**：打造自學者的「現代化 LLM 與 AI Agent 互動講義庫」，拒絕一次性靜態網頁，建立具備高度延展性、標準化、可重複依循的互動知識庫系統。
2. **產物形式**：純靜態、零打包負擔的 HTML5 + CSS3 + Vanilla JS，支援 GitHub Pages 與本機雙擊直開。
3. **頁面結構**：
   - 全站入口：`index.html`（講義卡片清單、即時搜尋、分類過濾器、學習進度指示）。
   - 各單元講義：`lessons/<kebab-case-slug>/index.html`（自我包含、麵包屑導航、學習目標、核心直覺、**互動沙盒 Widget**、實戰程式碼、折疊思考題、分頁按鈕）。
4. **設計系統**：
   - 品牌色票：`--primary: #2563EB`, `--accent-purple: #7C3AED`, `--accent-emerald: #059669`, `--bg-page: #F8FAFC`。
   - 字體規範：Inter、Noto Sans TC、JetBrains Mono。中文一律全形標點（，。、：！？「」）。
5. **AI 新增內容 SOP**：
   - Step 1: 確立主題與分配英文小寫 slug（如 `lessons/<slug>/`）。
   - Step 2: 套用 `AGENTS.md` 第 6 節標準骨架樣板撰寫 `index.html`，必備互動沙盒。
   - Step 3: 回填並註冊至首頁 `index.html` 的卡片列表與計數器。
   - Step 4: 同步更新 `log.md`（歷程記錄）與 `NOTES.md`（現況白板）。

詳細規範請隨時查閱同目錄下的 `AGENTS.md`。
