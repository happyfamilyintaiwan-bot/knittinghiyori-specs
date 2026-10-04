# poem.knittinghiyori.com 規範

**版本：poem-v0.1.1｜2026-10-04｜由 subdomain-monetization-notes（2026-09-28）整理，待 Zoe 補完**
負責人：Zoe。先讀 `core.md`；本檔只寫 poem 專屬的部分。

> 目前只有變現與 repo 的紀錄，GA4 追蹤寫法尚未整理。標 ⚠ 處待補，補完升 v1.0。

---

## 1. repo 與產生方式

- repo：`happyfamilyintaiwan-bot/poem`（CNAME `poem.knittinghiyori.com`）。
- **頁面由 `build.py` 從 `poems.json` 產生（需 Python 3.12+）**。改版面要改 `build.py` 再重跑；直接改 `index.html` 會被覆蓋。
- Drive（`emrld.ltd/NTc4NjIw.js?t=578620`）寫在 `build.py` 的 `DRIVE`，所有頁面都有。

## 2. AdSense

| 項目 | 規則 |
|---|---|
| slot | `6629751780` |
| 自動廣告 | 不開（載入碼不帶 `?client=`），所有連結加 `data-google-vignette="false"` |
| 位置 | **只放首頁**：日曆／借書卡之後、about 頁尾之前 |
| 不放 | 每日詩頁（`/MMDD/`） |

## 3. GA4

- ⚠ 內容 id 參數、`content_group`（建議 `poem`）、`page_title` 格式、事件清單待補。
- 新增參數前先查 core §3-4。

## 4. 待補

- GA4 追蹤寫法（§3）
- 版型規則
- 驗收與部署步驟
