# knittinghiyori-specs

knittinghiyori.com 與 tools／games／story／poem 子網域的**唯一**追蹤與版型規範。Zoe、Alison 兩個 AI 帳號開工前都讀這裡，收工後有改動都更新到這裡。

## 檔案

| 檔案 | 內容 | 負責人 | 修改規則 |
|---|---|---|---|
| `core.md` | 全站共用：固定 ID、GA4 原則與參數字典、AdSense、聯盟、Cookie、SEO、工程原則、驗收 | 共同 | 改動需對方確認 |
| `registry.md` | 所有工具／遊戲／作品的 id、前綴、狀態、待修清單 | 共同 | 加新列可直接加；改既有列需對方確認 |
| `tools.md` | tools 子網域 | Zoe | 改規則需 Zoe 確認；兩邊都可依規範新增工具 |
| `blog.md` | WordPress 部落格 | Zoe | 負責人直接改 |
| `games.md` | games 子網域 | Alison | 負責人直接改 |
| `story.md` | story 子網域（原創故事、小說分析、追劇） | Alison | 負責人直接改 |
| `poem.md` | poem 子網域 | Alison | 負責人直接改 |
| `CHANGELOG.md` | 每次改了什麼 | 共同 | 每次修改都要寫，新的在最上面 |

衝突時：**core 優先**於各站檔案。

## 使用循環

1. **開工**：AI 讀 core、registry、CHANGELOG＋對應站別檔案，第一句回報版本號與 CHANGELOG 最新一筆。
2. **收工**：有新規則、新 id、狀態改變 → AI 輸出「規範更新包」→ 貼到這個 repo（貼之前重新整理頁面）。
3. 改到 `core.md` 或 registry 既有列 → 先請對方確認。

## 版本號

- 中版號（v1.0→v1.1）：影響追蹤數據或上線頁面的改動。
- 小版號（v1.0→v1.0.1）：文字修正、⚠ 項目核對完成。
