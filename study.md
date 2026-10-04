# study.knittinghiyori.com 規範

**版本：study-v0.1｜2026-10-04｜Alison 提案、Zoe 定案**
內容負責人：Alison；上架：Zoe（見 core §0）。先讀 `core.md`；本檔只寫 study 專屬的部分。

## 1. 網址與檔案

| 項目 | 規則 |
|---|---|
| 首頁 | `study.knittinghiyori.com/`，依 kind 分「公開課」「自學」「上過的課」三區，最下面「想學清單」 |
| 主題卡 | 目前直接連該主題的部落格主力文章（`topics.json` 的 `blog`）；該主題有筆記後改連主題頁 |
| 主題頁 | `/<topic>/`，topic＝`topics.json` 的 id＝`notes/` 底下的資料夾名；沒有筆記時放「先讀部落格文章」按鈕 |
| 筆記頁 | `/<topic>/<英文-slug>/`，slug＝筆記檔名 |
| 原稿 | `notes/<topic>/<slug>.md`（Markdown＋開頭 title／date／summary／source） |
| 產生頁面 | `python3 build.py` 產生全部 HTML、sitemap、404，並做上線前檢查；產生的檔案不手改 |
| 頁首品牌列 | core §7：正式 logo＋「編織日和・學習筆記」，連 study 首頁 |
| 404 頁 | `404.html`：品牌列＋說明＋「回學習筆記首頁」＋最近更新＋全部主題卡；`noindex`、有 GA4（page_title `筆記\|404\|找不到頁面`） |
| 設計 | 日系清新筆記風：紙張米白底、方格／橫線筆記紙紋理、紙膠帶與便利貼點綴；色彩與字型寫在 `assets/study.css` 開頭的變數 |
| 語言 | 目前只有中文 |

## 2. 廣告

- 不開自動廣告：AdSense 載入碼不帶 `?client=`，所有連結加 `data-google-vignette="false"`（build.py 自動加）。
- 每頁最多 1 個手動版位，放在內容最下面、頁尾上面；slot 建立前不放。

## 3. GA4

| 項目 | 值 |
|---|---|
| `content_group` | `study` |
| 內容 id 參數 | `topic`（首頁、404 送 `hub`）；需在 GA4 註冊成事件範圍自訂維度 |
| `page_title` | `筆記\|主題名\|筆記標題`，主題頁 `筆記\|CS50\|主題總覽`，首頁 `筆記\|學習筆記\|總覽`，404 `筆記\|404\|找不到頁面` |

事件只用 core 共用事件 `cta_click`：

| cta_id | 位置 | cta_type |
|---|---|---|
| `brand_hub` | 頁首品牌列 | study |
| `topic_card` | 首頁主題卡（目前連部落格文章） | article（改連主題頁後用 study） |
| `blog_link` | 主題頁「先讀部落格文章」按鈕 | article |
| `course_link` | 主題頁「課程官網」按鈕 | other |
| `source_link` | 筆記頁來源連結 | other |
| `notfound_hub` | 404「回學習筆記首頁」 | study |
| `notfound_topic` | 404 主題卡 | 同 `topic_card` |

## 4. 驗收

core §9 全部項目；`build.py` 已自動檢查：GA4、spec-version、不帶 `?client=`、vignette、空連結、icon、品牌列、追蹤碼和號、JSON-LD 可解析。390px／1200px 溢出與對比要另外看。
