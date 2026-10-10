# knittinghiyori.com（WordPress 部落格）規範

**版本：blog-v1.1｜2026-10-10**（v1.1：新增 §4 GA4 追蹤，給搬到 Astro 的新站用）
負責人：Zoe＋Alison（兩人都會寫文章；改本檔規則時通知對方）。先讀 `core.md`。

---

## 1. WordPress 內嵌程式（自訂 HTML 區塊）

### 為什麼
- wptexturize 會把 `<script>` 裡的 `&&`、`>` 改成 `&#038;`、HTML 代碼，整支程式失效（2026-09-24 行李清單、旅費分帳；2026-09-25 聚餐分帳都發生過）。
- Autoptimize 會改寫內嵌 script，管理員登入時甚至整段內容消失。
- 站上另有 Asset CleanUp、EWWW lazy load、Bluehost nfd performance、Advanced Ads，都可能改動內嵌程式。

### 一律這樣做
- 主程式先 base64 編碼，再用一小段**不含 `&`、`<`、`>`** 的載入器解碼執行（atob＋TextDecoder）。
- 聯盟連結放載入器裡的設定物件（例：`window.TS_AFF`、`window.BS_AFF`、`window.KHP_LINKS`），明文、網址不含 `&`。
- script 前後包 `<!--noptimize-->…<!--/noptimize-->`，並加 `data-cfasync="false" data-no-optimize="1" data-no-defer="1" nowprocket`。
- HTML 註解裡不寫任何標籤字樣。
- 選項按鈕直接寫在 HTML，不靠 JS 產生。
- 浮動元素（toast、modal、浮動列）執行時移到 `<body>` 底下。
- 原始碼與 `build.py` 放工作區，不直接在 WordPress 編輯。

### 上線檢查
- 未登入：`fetch(頁面, {credentials:'omit'})`，確認主程式可以 `new Function()` 編譯。
- 已登入：比對 `?ao_noptimize=1` 版本。
- 更新後清 Autoptimize 快取。

## 2. WordPress 工具頁的多語

- 同頁切換中／EN／日本語，Google 只收錄中文；外語模式收起中文 SEO 文章區。
- 語言優先順序：上次選的語言 → 分享連結 `l=en／ja` → 打開別人分享內容時依瀏覽器語言 → 中文。
- 搬到 tools 子網域後改用三個網址（見 `tools.md` §7）。

## 3. 轉址

- 工具搬家用 Rank Math 301，原頁 noindex（步驟見 `tools.md` §7）。

## 4. GA4 追蹤（Astro 新站；WordPress 舊頁面沒有這些事件）

實作：knittinghiyori-site repo 的 `public/js/hy-track.js`。事件與參數照 `core.md` §3。

- `content_group`：文章 `article`；`/tools/`、`/en/en-tools/` 的工具頁 `tool`。
- `page_lang`：`zh-Hant`／`en`／`ja`。
- `page_title`：`文章|主題|文章標題`（上限 100 字元）。主題用電子報的主題名（旅遊、AI、信用卡、日股美股、編織、劇評、書評、西洋棋、日文學習、部落格經營、艾立森出走中、CS、APP、字帖、其他）。工具頁 `工具|名稱`、其他頁面 `頁面|名稱`、404 `文章|找不到頁面|404`。只影響 GA4 報表，網頁與搜尋結果的標題不變。
- 點擊一律 `cta_click`，`cta_id` 記位置：

| 位置 | cta_id |
|---|---|
| 頁首品牌列 | `brand_hub` |
| 桌面選單 | `nav_menu` |
| 手機選單（分類／工具／子網站／語言／底部） | `menu_category`／`menu_tool`／`menu_site`／`menu_lang`／`menu_footer` |
| 麵包屑 | `breadcrumb` |
| 本篇目錄 | `toc` |
| 文內延伸閱讀 | `inline_related` |
| 文末相關文章卡片 | `related_card` |
| 系列上一篇／下一篇／系列目錄 | `series_prev`／`series_next`／`series_hub` |
| 文末訂閱框／訂閱中心 | `newsletter_box`／`newsletter_hub`（`cta_type=newsletter`） |
| 作者框 | `author_box` |
| 首頁最多人閱讀／文章清單 | `home_top10`／`post_list` |
| 內文裡的聯盟連結 | `article_affiliate`（`cta_type` 填平台名） |
| 內文裡連到電子報、工具、子網站 | `article_body` |
| 頁尾 | `footer` |
| 404 | `notfound_hub`、`notfound_article`、`notfound_site` |

- 內文裡一般的站內文章連結不記（數量太多）。
- `read_depth`：讀到內文 50％、90％ 各送一次，`pct` 為 50／90；內文高度不到 600px 的頁面不送。
- `faq_open`：內文裡的 `<details>`（不含本篇目錄），`option` 用 `q1`、`q2`…。
- `share`：新站目前沒有分享按鈕，加了按鈕再照 core §3-2 送。
- 除錯：網址加 `?hy_debug=1`，Console 印 `[hy-blog]`。

## 5. ⚠ 待補


- AdSense 在部落格的設定（自動廣告？slot？）、Travelpayouts 在部落格的用法、文章 SEO 標題格式。
