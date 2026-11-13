# LLM Dive Hub - 變更與決策歷史日誌 (Log)

本文件以時間先後順序（Append-only）記錄專案所有的重要架構決策、單元擴充與視覺系統改動。
每次新增或修改內容時，AI 與人類協作者必須在此處追加一筆紀錄，以便任何接手者快速了解演進歷史。

---

## [2026-11-13] feat | 初始化專案與確立三大標準講義單元
- 制定 `AGENTS.md` 與 `CLAUDE.md` 專案憲法，定義「互動式講義標準結構」與「AI 新增頁面 4 步驟 SOP」。
- 建立全站共用設計系統 `assets/css/global.css`（定義現代科技感色票、WCAG 對比度字級、卡片陰影）。
- 建立入口首頁 `index.html` 與動態互動腳本 `assets/js/main.js`（支援標籤即時篩選、全文關鍵字即時搜尋、閱讀進度徽章）。
- 完成講義單元一 `lessons/transformer-attention/`：
  - 主題：直覺理解 Self-Attention 與 Multi-Head 機制。
  - 核心互動：可點選詞彙動態觀察 Query-Key-Value 矩陣計算與 Softmax 注意力熱圖分佈。
- 完成講義單元二 `lessons/rag-system-design/`：
  - 主題：現代 RAG 系統設計（Chunking、混合檢索與重排序）。
  - 核心互動：可調節 Chunk Size、切換向量與關鍵字檢索模式，實時預覽檢索精準度與召回率變化。
- 完成講義單元三 `lessons/llm-agent-patterns/`：
  - 主題：AI Agent 核心模式與 Karpathy LLM Wiki 實戰。
  - 核心互動：ReAct 決策循環模擬器（動態演繹 Thought → Action → Observation 逐步執行）。
- 建立 `.nojekyll` 與 `README.md`，為 GitHub Pages 部署做準備。
