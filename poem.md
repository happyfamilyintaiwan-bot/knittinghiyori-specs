# poem.knittinghiyori.com 規範

**版本：poem-v0.2｜2026-10-06｜Zoe（v0.2：Drive、AdSense、頁尾 Cookie 說明、spec-version 實際上線；新增 404 頁。v0.1.1：由 subdomain-monetization-notes 整理）**
負責人：Zoe。先讀 `core.md`；本檔只寫 poem 專屬的部分。

> GA4 追蹤寫法尚未整理。標 ⚠ 處待補，補完升 v1.0。

---

## 1. repo 與產生方式

- repo：`happyfamilyintaiwan-bot/poem`（CNAME `poem.knittinghiyori.com`）。
- **頁面由 `build.py` 從 `poems.json` 產生（需 Python 3.12+）**。改版面要改 `build.py` 再重跑；直接改 `index.html` 會被覆蓋。
- Drive（`emrld.ltd/NTc4NjIw.js?t=578620`）寫在 `build.py` 的 `DRIVE`，所有頁面（含 404）head 第一個 script。
- 常數都在 `build.py` 開頭：`DRIVE`、`AD_CLIENT`／`AD_SLOT`、`SPEC`（spec-version，目前 `core-v1.3/poem-v0.2`）、`PRIVACY`。升版時改 `SPEC` 再重跑 build。
- 頁面一律經 `write()` 寫出：自動在所有 `<a>` 加 `data-google-vignette="false"`（靜態 HTML，不靠 JS）。新增頁面也要用 `write()`。
- 每頁最下方有 `.kh-legal`（三語，`legal()` 產生，文字照 core §6）。
- `404.html` 由 `build_404()` 產生：noindex、不放 canonical／hreflang／OG；GA4 `story_id` = `poem-404`；回目錄 `notfound_home`、最近 3 首 `notfound_poem`。
- 跑 build 會重畫所有 og.png（檔案有細微差異），沒改到的舊詩 og.png 用 `git restore` 還原。

## 2. AdSense

| 項目 | 規則 |
|---|---|
| slot | `6629751780` |
| 自動廣告 | 不開（載入碼不帶 `?client=`），所有連結加 `data-google-vignette="false"`；AdSense 後台 poem 子網域的自動廣告也要是關閉 |
| 位置與數量 | **只放首頁 1 個**：日曆／借書卡之後、about 之前（`ad_unit()`），上下各留 150px |
| 載入碼 | 只在首頁 head 輸出（`head(..., ads=True)`） |
| 不放 | 每日詩頁（`/MMDD/`）、404（載入碼也不放） |
| 小標與頁尾文字色 | `--note`：白天 `#6b6359`（對 `#f1ece1` 對比 5.02），夜間沿用 `--pencil`（5.97）。網站原本的 `--pencil` 白天只有 3.16，新元素不要用 |

## 3. GA4

- ⚠ 內容 id 參數、`content_group`（建議 `poem`）、`page_title` 格式、事件清單待補。
- 新增參數前先查 core §3-4。

## 4. 待補

- GA4 追蹤寫法（§3）
- 版型規則
- 驗收與部署步驟
- 頁首品牌列（core §7，registry 待修清單）
- 既有元素對比不足：`--pencil` 白天 3.16、電子報按鈕 `#c8707e` 3.26
