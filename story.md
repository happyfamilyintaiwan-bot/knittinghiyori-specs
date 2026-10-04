# story.knittinghiyori.com 規範

**版本：story-v1.2｜2026-10-04｜v1.2：作品頁統一用 hy-story.js，送 content_group=story、work；莫斯科紳士上線。v1.1：分工改為追劇／漫畫 Zoe、小說 Alison；新增漫畫類型；原創追劇不開自動廣告**
負責人：追劇（drama）與漫畫（comics）由 Zoe 負責，小說（novel）由 Alison 負責；story 首頁 hub 外框與本檔共用段落由兩人共管，改的時候兩人都要確認，各區卡片由該區負責人維護。先讀 `core.md`；本檔只寫 story 專屬的部分。

> 整合時有 7 處和 core 衝突，已依 core 改寫並經 Alison 確認，原寫法與理由見 §9。

---

## 1. 網址與歸屬

| 項目 | 規則 |
|---|---|
| 網址 | `story.knittinghiyori.com/<類別>/<英文作品名>/`，資料夾＋`index.html`；英日版放作品資料夾裡（`/en/`、`/ja/`） |
| 類別資料夾 | `books/`＝書與小說（Alison）、`drama/`＝影視劇集，含原創追劇（Zoe）、`comics/`＝漫畫（Zoe）。資料夾就代表負責人；作品名本身不加 `book-`／`drama-` 前綴 |
| Hub | story 首頁（`story` repo）就是 hub，分「小說」「追劇」「漫畫」三區卡片：小說區由 Alison 維護，追劇區、漫畫區由 Zoe 維護；hub 外框（版型、頁首頁尾、追蹤碼）兩人共管。不另做 WordPress hub 文章 |
| 新作品放哪 | 上傳到 `story` repo 對應的類別資料夾，**不開新 repo**。2026-10-04 起既有 7 部追劇（含 5 部原創）搬進 `drama/`，舊網址保留轉址頁（canonical＋meta refresh＋一行文字連結），不要刪 |
| assets | `assets/<作品名>/`（og.png 等） |
| 既有 WordPress 頁 | 《環遊世界八十天》維持 `knittinghiyori.com/around-the-world-in-80-days-route/` 不搬，story 首頁小說區放外連卡片 |

所有作品都要在 `registry.md` 登記（work 值、類型、狀態）。

---

## 2. 頁面設定（`window.HIYORI`）

檔案底部 `window.HIYORI`：

| 欄位 | 填什麼 |
|---|---|
| `work` | 作品資料夾名（不含類別），例：`a-gentleman-in-moscow`（必填，每個事件都帶） |
| `ga4` | **`G-ZQZHTYTRMQ`**（全站共用，見 core §1；不另建 story 資源） |
| `adsense` | `ca-pub-2022028565680247` |
| `adSlots.top`／`.mid` | 都填 story 的 `2285424505`（同 tools 做法：所有版位共用一個 slot） |

欄位留空時的行為照舊：`ga4` 空 → 不載 gtag、`track()` 靜默跳過；`adsense` 空 → 不載廣告；slot 空 → 該版位隱藏。

`<head>` 照 core §2 順序，**story Drive 放第一個 script**、AdSense 載入碼**不帶 `?client=`**（理由見 §9 #4）。

---

## 3. GA4

### 3-1 識別

| 項目 | 值 |
|---|---|
| 內容 id 參數 | **`work`**（作品資料夾名，英文小寫＋連字號） |
| `content_group` | `story`（2026-10-04 起 hy-story.js 預設送；之前追劇送 `interactive-story`，看長期趨勢要合併） |
| `page_title` | `小說\|作品名\|這頁在做什麼`、`追劇\|劇名\|這頁在做什麼`、`漫畫\|作品名\|這頁在做什麼`，例：`小說\|莫斯科紳士\|中英版本怎麼選` |

```js
gtag("set",{content_group:"story",work:"a-gentleman-in-moscow",page_lang:"zh-Hant",page_title:"小說|莫斯科紳士|中英版本怎麼選"});
```

- 所有作品頁（books／drama／comics）都載入 `/hy-story.js`，它負責：`gtag('set')` 的 `content_group=story`、`work`、`page_lang`（只送 zh-Hant／en／ja），以及互動頁共用事件 story_start、story_progress、section_view、interaction、story_complete、story_exit 和一般 `[data-cta]` 的 cta_click。`story_id` 是舊名稱，過渡期一起送，值和 `work` 相同。
- 頁面只需在 hy-story.js **之後**補 `page_title`（可以照上面的範例整行重設，值要一致）。
- 需要多帶參數的 CTA（例：購書要帶 `option`）用頁面自己的屬性（莫斯科紳士用 `data-gm-cta`），不要同時加 `data-cta`，避免 cta_click 重複。
- 會送 `interaction` 的元素（summary、按鈕）加 `data-interact="英文代碼"`；沒有的話 hy-story.js 只送元素 id 或標籤名，不送畫面文字。
- 首頁作品卡片：`cta_click`、`cta_type=story`、`cta_id`＝卡片 id 或作品名。

### 3-2 小說頁事件

| 事件 | 何時觸發 | 參數 | 用途 |
|---|---|---|---|
| `cta_click` | 點購書按鈕 | `cta_id=buy_book`、`cta_type=shopee`（平台名）、`option`＝zh／en（哪個版本）、`link_url` | **聯盟轉換**。看中文版／英文版誰被點多 |
| `cta_click` | 點站外來源連結 | `cta_id=source_link`、`cta_type=other`、`link_url` | 來源標註是否被看見（網域從 link_url 看） |
| `quiz_complete` | 版本自測答完（每次瀏覽只送一次） | `score`（數字）、`result`＝zh／zh_then_en／en | 自測結果 vs. 實際點擊的版本 |
| `progress_check` | 放開閱讀進度拉桿 | `pct`（數字）、`option`＝seg0／seg1／seg2／seg3 | 讀者卡在哪一段 → 下一篇寫什麼 |
| `faq_open` | 展開 FAQ | `option`＝題目英文代碼 | 高點擊題目獨立成文 |
| `share`／`export` | 照 core §3-2 | | |

- `quiz_complete`、`progress_check` 是 story 共用事件（所有作品同名），不加前綴。
- 追劇頁沿用同一套；該頁特有互動用 `{前綴}_{動詞}`，前綴先到 `registry.md` 登記（例：集數地圖 `ep_view`，不用無前綴的 `episode_view`）。
- `score`、`pct` 是數字，照送不註冊；要進報表時再註冊成自訂指標。

### 3-3 GA4 後台

1. **只需註冊 1 個自訂維度**：`work`（事件範圍）。`option`、`result`、`cta_id`、`cta_type` 都已註冊。
2. 關鍵事件：`cta_click` 已是關鍵事件，不用另設。要單看購書轉換，報表篩 `cta_id=buy_book`。
3. GA4 不另建資源（共用 G-ZQZHTYTRMQ）。GSC：主站若是網域資源已涵蓋 story；若是網址前置字元資源，另外新增 `https://story.knittinghiyori.com/`。

---

## 4. AdSense（小說頁）

| 位置 | 原因 |
|---|---|
| top：「打到我的瞬間」之後、閱讀進度地圖之前 | 讀完個人段落的自然停頓點 |
| mid：誠實揭露之後、FAQ 之前 | 與 tools 規範一致 |
| **不放**：自測、版本比較表、購書按鈕附近（上下至少 150px） | 誤點風險；會吃掉聯盟轉換 |

- 每頁最多 2 個；所有 `<a>` 加 `data-google-vignette="false"`。
- **關掉自動廣告要做兩步**：① 載入碼不帶 `?client=`；② AdSense 後台「自動廣告 → 網頁排除」加入 `story.knittinghiyori.com/<作品名>/`。上線後實測確認沒有自動廣告（錨定、插頁）出現。
- 揭露段加一行 AdSense 說明；頁尾放 `.kh-legal`（core §6）。

---

## 5. 版型與 SEO

- 白底黑字＋單一強調色，只有淺色主題。**每部作品自己定色與字體**，CSS 前綴各自命名（莫斯科紳士 `.gm-`）。
- 中文內文走系統字，標題可載 Noto Serif TC（用 `&text=` 子集）。
- favicon 用編織日和系列（core §7）。
- `<title>`（SEO 標題）與 H1 不同。
- JSON-LD：小說頁 `Article`（about → Book）＋`Book`＋`FAQPage`（與頁面逐字一致）＋`BreadcrumbList`（Story. → 作品）；追劇頁 `TVSeries`。漫畫頁 ⚠ 待 Zoe 決定（例：`ComicSeries`）。
- 子網域沒有 WordPress 的改寫問題，頁面 JS 可以正常寫；**GA4 追蹤碼仍不含「和號」字元**（core §3-1 #7）。
- 互動元件慣例：閱讀進度地圖有 JS 時只顯示選中那一段（`.gm-map-js`），沒有 JS 時全部段落顯示；版本自測有 JS 時答完才顯示唯一一個對應結果（`.gm-quiz-js`），沒有 JS 時所有結果顯示。兩者都讓爬蟲讀得到全部文字。

---

## 6. 驗收

core §9 全部，再加：

- 390px／1200px × 初始／互動後（自測作答、拉桿、FAQ）。
- 未填 ID 時廣告位 0 個顯示。

莫斯科紳士（2026-10-04，/books/）已驗：390／1200 溢出 0、進度地圖只顯示 1 段、自測直接給唯一結果、dataLayer 事件無重複且無中文、和號 0、JSON-LD 可解析、廣告距互動元件 ≥150px。上線後補 DebugView 實測。

---

## 7. 部署（新作品）

1. 在 `registry.md` 登記 `work`。
2. 作品資料夾放進 story repo 對應的類別資料夾（`books/`／`drama/`／`comics/`），不開新 repo。
3. 本機測：`python3 -m http.server 8000`，跑 §6 驗收。
4. 填 `window.HIYORI`。
5. `sitemap.xml` 加一筆。
6. story 首頁對應區塊加卡片。
7. GSC 要求建立索引。
8. Travelpayouts 後台確認 Drive。
9. AdSense 後台把這個作品網址加入自動廣告的網頁排除。

---

## 8. 待補

- 既有原創故事（the-early-spring、confession、when-i-meet-the-moon、hidden-love、the-first-frost）的追蹤寫法：依《故事 GA4 v1.5》，原文未找到；用 DebugView 核對後補進本檔
- `content_group` 確認是 `story`

---

## 9. 整合時依 core 改寫的地方（給 Alison 確認）

| # | 原 v1 寫法 | 改成 | 理由 |
|---|---|---|---|
| 1 | `ga4` 填「story 子網域的 GA4 評估 ID」，主站不涵蓋要另建 | 填 `G-ZQZHTYTRMQ` | 全站共用一個資源，跨站導流與比較才看得到；子網域 cookie 共用 |
| 2 | `affiliate_click`＋`network`、`partner` | `cta_click`＋`cta_id=buy_book`、`cta_type=shopee`、`option=zh/en` | core 統一聯盟點擊寫法；省下 2 個自訂維度名額 |
| 3 | `faq_open` 帶 `question` | 帶 `option` | 全站同一參數 |
| 4 | 未寫自動廣告；core 舊紀錄寫 story「開自動廣告」 | 小說、追劇、漫畫頁（含 5 部原創追劇）**不帶 `?client=`**、只放手動單元 | 自動廣告無法保證避開自測與購書按鈕；不帶 `?client=` 的頁面不會跑自動廣告，不影響 story 首頁 |
| 5 | `source_click`＋`source_domain` | `cta_click`＋`cta_id=source_link` | 不多開事件與參數；網域可從 link_url 看 |
| 6 | `progress_check` 帶 `segment` | 帶 `option`＝seg0–seg3 | 不多佔自訂維度 |
| 7 | 註冊 3 個自訂維度（work、partner、result） | 只註冊 `work` | 其他已註冊或已改用既有參數 |
| — | 沒提 Travelpayouts Drive | 照 core 放 story Drive | core：所有頁面都放 |
| — | 「沿用 tools 子網域規範 v1」 | 改為「先讀 core.md」 | tools v1 已被 core＋tools.md 取代 |
