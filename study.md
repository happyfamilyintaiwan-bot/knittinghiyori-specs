# study.knittinghiyori.com 規範

**版本：study-v0.4｜2026-10-10｜Alison 提案、Zoe 上架**（v0.4：新增互動頁規則（整頁 HTML、中英雙語）、聯盟連結規則、互動頁事件 studio_；首例 artists-way/abundant-studio。v0.3：開 AdSense 底部版位與 Travelpayouts Drive、專屬分享縮圖、404 對齊 core v1.4。v0.2：設計改中性專業調性、首頁加「目次」`toc_link`。v0.1：Alison 提案、Zoe 定案）
內容負責人：Alison；上架：Zoe（見 core §0）。先讀 `core.md`；本檔只寫 study 專屬的部分。

## 1. 網址與檔案

| 項目 | 規則 |
|---|---|
| 首頁 | `study.knittinghiyori.com/`，開頭右側「目次」（桌機才顯示，編號＝卡片左上的 01～）；依 kind 分「公開課」「自學」「上過的課」三區，最下面「想學清單」 |
| 主題卡 | 目前直接連該主題的部落格主力文章（`topics.json` 的 `blog`）；該主題有筆記後改連主題頁 |
| 主題頁 | `/<topic>/`，topic＝`topics.json` 的 id＝`notes/` 底下的資料夾名；沒有筆記時放「先讀部落格文章」按鈕 |
| 筆記頁 | `/<topic>/<英文-slug>/`，slug＝筆記檔名 |
| 原稿 | `notes/<topic>/<slug>.md`（Markdown＋開頭 title／date／summary／source） |
| 產生頁面 | `python3 build.py` 產生全部 HTML、sitemap、404，並做上線前檢查；產生的檔案不手改 |
| 頁首品牌列 | core §7：正式 logo＋「編織日和・學習筆記」，連 study 首頁 |
| 404 頁 | `404.html`，照 core §7：品牌列＋說明＋「回學習筆記首頁」＋最近更新＋全部主題卡＋跨站連結一行；網址含 `/en/`、`/ja/` 時說明與按鈕換英文／日文；`noindex`、不放 canonical／OG／廣告單元；page_title `筆記\|找不到頁面\|404` |
| 設計 | 日系筆記本骨架＋中性專業調性（照顧男女讀者）：點陣方格底、明朝體標題（Noto Serif TC）、等寬編號（IBM Plex Mono）、方正卡片＋左上索引標籤、筆記頁左側紅色邊線；不用紙膠帶、便利貼、手寫字、歪斜卡片這類偏可愛的元素。色彩與字型寫在 `assets/study.css` 開頭的變數 |
| 分享縮圖 | `icons/og-study.jpg`（1200×630）：左上正式 logo＋「編織日和・學習筆記」、標題、目次、網址；全站共用一張。換圖用新檔名（`og-study-2.jpg`…），改 `build.py` 的 `OG_IMG`；`og:image:alt` 開頭寫品牌名 |
| 語言 | 預設只有中文；互動頁可做中英雙語：中文 `/<topic>/<slug>/`、英文 `/en/<topic>/<slug>/`（core §7 預設），互設 hreflang，x-default 指中文 |
| 互動頁 | 不經 Markdown 的整頁 HTML。產生器原始碼放 `interactive/<slug>/`（自己的 `build.py` 輸出到 `dist/`），在 `topics.json` 該主題加 `page`（href、title、label、source、langs）；study 的 `build.py` 會執行產生器、把 `dist/` 原樣放進網站、補 vignette 標記、加進 sitemap 並照常做上線前檢查。spec-version、Drive、AdSense slot 由 study 的 `build.py` 用環境變數帶入（`HY_SPEC`、`HY_DRIVE`、`HY_ADS_CLIENT`、`HY_ADS_SLOT`），產生器不各自維護。有 `page` 的主題，首頁卡片、目次、404 卡片直接連互動頁。首例 `artists-way/abundant-studio` |

## 2. 廣告

- 不開自動廣告：AdSense 載入碼不帶 `?client=`，所有連結加 `data-google-vignette="false"`（build.py 自動加）。
- 每頁最多 1 個手動版位（單元「Study-頁面底部」，slot 見 core §1），放在內容最下面、頁尾上面；404 不放。
- Travelpayouts Drive 放 `<head>` 第一個 script，所有頁面含 404，寫法同 tools（含 `data-cmp-ab`）。
- 聯盟連結：每頁最多 2 個位置；蝦皮只放中文頁；`rel="sponsored nofollow noopener"`，區塊下方寫揭露。

## 3. GA4

| 項目 | 值 |
|---|---|
| `content_group` | `study` |
| 內容 id 參數 | `topic`（首頁、404 送 `hub`）；需在 GA4 註冊成事件範圍自訂維度 |
| `page_title` | `筆記\|主題名\|筆記標題`，主題頁 `筆記\|CS50\|主題總覽`，首頁 `筆記\|學習筆記\|總覽`，404 `筆記\|找不到頁面\|404` |

事件只用 core 共用事件 `cta_click`：

| cta_id | 位置 | cta_type |
|---|---|---|
| `brand_hub` | 頁首品牌列 | study |
| `toc_link` | 首頁「目次」（桌機） | 同 `topic_card` |
| `topic_card` | 首頁主題卡（目前連部落格文章） | article（改連主題頁後用 study） |
| `blog_link` | 主題頁「先讀部落格文章」按鈕 | article |
| `course_link` | 主題頁「課程官網」按鈕 | other |
| `source_link` | 筆記頁來源連結 | other |
| `page_link` | 主題頁「互動頁」按鈕 | study |
| `read_card` | 互動頁「閱讀本週章節」卡片的買書連結 | shopee（`option`＝書的代碼） |
| `book_shelf` | 互動頁書架區 | shopee（`option`＝書的代碼） |
| `notfound_hub` | 404「回學習筆記首頁」 | study |
| `notfound_topic` | 404 主題卡 | 同 `topic_card` |
| `notfound_site` | 404 跨站連結 | story／game／tool／article／other（詩） |

### 3-1 互動頁事件（artists-way/abundant-studio，前綴 studio_）

| 事件 | 何時 | 參數 |
| --- | --- | --- |
| `studio_start` | 按「搬進工作室」 | `level`=l01、`entry_point`（direct／shared，網址帶 `?from=invite` 為 shared） |
| `studio_pages_done` | 完成當天晨間隨筆（一天一次） | `level`=l01–l12（週次）、`option`=paper／typed／short |
| `studio_streak` | 連續天數達 7、30 | `milestone`=s7／s30 |
| `studio_date_done` | 本週藝術家約會完成 | `level` |
| `studio_walk_done` | 本週獨自散步完成 | `level` |
| `studio_week_complete` | 搬進本週物件 | `level`、`item_count`（本週隨筆天數）、`score`（本週練習完成數） |
| `studio_progress_reset` | 清除進度 | `level` |

- 共用事件：`share`／`share_cancel`（`content_type=study`）、`faq_open`（`option`=q1–q7）、`lang_switch`（`source`=header）、`cta_click`（`brand_hub`、`read_card`、`book_shelf`）。
- 隨筆文字不送、不存，只記完成日期。
- 書的代碼：`artists_way`（創作之路）、`creative_act`（創造力的修行）。

## 4. 驗收

core §9 全部項目；`build.py` 已自動檢查：GA4、spec-version、不帶 `?client=`、vignette、空連結、icon、品牌列、追蹤碼和號、JSON-LD 可解析。390px／1200px 溢出與對比要另外看。
