# LLM Dive Hub - 現況白板與待辦事項 (NOTES)

本文件是專案的「即時現況與交接白板」。隨時改寫、保持簡潔。
工作結束前務必更新本檔案，確保下次接手時知道「目前狀態」與「下一步從哪裡開始」。

---

## 📌 目前狀態 (Current Status)
- [x] 完成專案規範文件 `AGENTS.md` 與 `CLAUDE.md`。
- [x] 完成全域設計系統與 CSS 樣式庫 (`assets/css/global.css`)。
- [x] 完成入口首頁 `index.html`（含即時搜尋、分類篩選、自適應卡片網格）。
- [x] 完成講義單元一：Self-Attention 機制（含互動式注意力矩陣計算模擬器）。
- [x] 完成講義單元二：現代 RAG 系統設計（含互動式 Chunk 切換與檢索模擬器）。
- [x] 完成講義單元三：AI Agent 模式與 LLM Wiki（含互動式 ReAct 循環動態展示）。
- [x] 本地靜態頁面相容性測試完成（所有連結使用相對路徑，零構建依賴）。
- [ ] 專案推播至 GitHub Repository 並啟用 GitHub Pages 公開存取。

---

## 🚀 下一次接手建議起點 (Next Steps)
1. **GitHub Pages 上線**：上傳至 GitHub，並在 Repository Settings > Pages 啟用部署。
2. **預計擴充之單元清單 (Backlog)**：
   - `lessons/lora-finetuning/`：LoRA 參數高效微調與低秩矩陣分解直覺解析。
   - `lessons/prompt-engineering-patterns/`：結構化 Prompt 模式（Few-shot、Chain-of-Thought、System Prompt 拓撲）。
   - `lessons/evaluation-benchmarks/`：LLM 評測指標解析（MMLU, GSM8K, SWE-bench 避坑指南）。

---

## 💡 開發備忘 (Reminders for AI)
- 每次新增新講義時，務必遵循 `AGENTS.md` 的 4 步驟 SOP，別忘了在 `index.html` 的列表追加新卡片！
- 中文一律使用全形標點符號（，。、：！？「」）。
- 維持純靜態原則，不引入需要 npm build 的肥大套件。
