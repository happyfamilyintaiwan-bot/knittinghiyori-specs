# 內容 ID 與事件前綴登記表（registry）

**版本：registry-v1.1｜2026-10-04｜Zoe＋Alison**

規則：
- 新工具／遊戲／作品**開工前**先在這裡加一列，前綴不可與表中任何一列重複（工具、遊戲共用前綴空間）。
- 加新列：兩邊都可以直接加，寫 CHANGELOG。
- 改既有列（改 id、改前綴）：原則上不改；真的要改，需要另一位確認，因為會切斷 GA4 歷史資料。
- 狀態只用：`規劃中`／`已上線`／`已搬家`／`待修`／`擱置`。
- ⚠＝尚待用 `?hy_debug=1`＋DebugView 確認。
- 各列的負責人依 core §0「負責分工」；放錯子網域的項目在備註標「轉移中」。

---

## 工具（content_group=tool，id 參數 `tool_id`）

| tool_id | 名稱 | 網址 | 前綴 | page_title | 狀態 | 備註 |
|---|---|---|---|---|---|---|
| `hub` | 工具總覽頁 | tools / ・/en/ ・/ja/ | `hub_` | `工具\|工具總覽\|免費線上小工具` | 已上線 | 與遊戲 `hub_` 同名，靠 tool_id 區分 |
| `travel_split` | 旅費分帳計算機 | tools /travel-split-calculator/（三語） | `split_` | `工具\|旅費分帳計算機\|出國多幣別分帳` | 已搬家 | WP 待設 301 |
| `bill_split` | 聚餐分帳計算機 | WP /tools/bill-split-calculator/ | `bill_` | ⚠ 待補 | 已上線 | |
| `parking_timer` | 停車計時卡 | tools /parking-timer/（只有中文） | `park_` | `工具\|停車計時卡\|算停車費與限停倒數` | 已上線 | Alison 製作 |
| `concert_trip` | 追星遠征規劃器 | tools /concert-trip-planner/（只有中文） | `ct_` | `工具\|追星遠征規劃器\|海外演唱會搶票與行程規劃` | 規劃中 | Alison 製作，定稿後上傳 tools repo 並加入 tools.json |
| `season_booking` | 季節訂房倒數工具 | tools /season-booking/ | ⚠ 定稿時確認 | ⚠ `工具\|…` | 規劃中 | 原規劃放 games，改由 Alison 直接在 tools 製作；games 不上線，不需要導向 |
| `ai_image_prompts` | AI 照片轉插畫風格指令 | tools /ai-image-prompts/ | `aip_` | `工具\|AI照片轉插畫\|風格指令` | 規劃中 | 尚未放進 tools repo |
| `trip_planner`（預定） | 旅遊行程共編工具 | WP /group-trip-planner/ | `tp_` | ⚠ 待補 | **待修** | 見下方「待修清單」；不在總覽頁 19 個工具裡，⚠ Zoe 決定是否加入 |
| `jr_pass`（預定） | JR Pass 計算機 | WP /tools/jr-pass-calculator/ | `jrpass_` | ⚠ 待補 | **待修** | 見下方「待修清單」 |
| `esim`（預定） | eSIM 比價工具 | WP /tools/esim-plan-picker/ | `esim_` | ⚠ 待補 | 已上線 | |
| `packing_list`（預定） | 出國行李清單產生器 | WP /tools/packing-list-generator/ | `packing_` | ⚠ 待補 | 已上線 | |
| `japanese_quest`（預定） | 日文學習資源＋30 天闖關 | WP /tools/japanese-quest/ | `njq_` | ⚠ 待補 | 已上線 | |
| `youtube_transcript`（預定） | YouTube 逐字稿產生器 | WP /tools/youtube-transcript/ | `kyt_` | ⚠ 待補 | 已上線 | |
| `knitting_needles`（預定） | 織女出國安檢查詢 | WP /knitting-needles-carry-on-rules/ | — | — | 已上線 | 文章型，先不搬 |
| `cube_miles`（預定） | 小樹點換哩程試算器 | WP /cube-tree-points-to-airline-miles-guide/ | — | — | 已上線 | 2028 前不搬 |
| `travel_deals`（預定） | 旅遊優惠總整理 | WP /tools/travel-deals/ | — | — | 已上線 | |
| `instant_camera`（預定） | 拍立得選擇工具 | WP /instant-camera-guide/ | — | — | 已上線 | 文章型，先不搬 |
| `kaomoji`（預定） | 大型顏文字產生器 | WP /tools/kaomoji-symbols/ | — | — | 已上線 | 2028 前不搬 |
| `ig_symbols`（預定） | IG 特殊符號 | WP /tools/ig-symbols/ | — | — | 已上線 | |
| `post_formatter`（預定） | 貼文排版小工具 | WP /tools/social-post-formatter/ | — | — | 已上線 | |
| `japan_stock`（預定） | 日股代號查詢 | WP /tools/japan-stock-ticker/ | — | — | 已上線 | |
| `dca`（預定） | 投資定期定額計算機 | WP /tools/dca-calculator/ | — | — | 已上線 | |
| `utm_builder`（預定） | UTM 快速生產工具 | WP /tools/utm-link-builder-wordpress/ | — | — | 已上線 | |
| `qr_code`（預定） | QR Code 產生器 | WP /tools/qr-code-generator/ | — | — | 已上線 | |
| `business_card_qr`（預定） | 名片 QR Code 產生器 | WP /tools/business-card-qr-code/ | — | — | 已上線 | |

「（預定）」＝總覽頁 `tools.json` 已在用的 id，WordPress 頁面實際送出的值還沒確認。搬家時以本表為準，順便改正頁面程式碼。前綴「—」＝目前沒有專屬事件。

---

## 遊戲（content_group=game，id 參數 `game_id`）

| game_id | 名稱（⚠＝請 Alison 補中文名） | 前綴 | 狀態 | 備註 |
|---|---|---|---|---|
| ⚠ `hub`？ | 遊戲主頁 | `hub_` | 已上線 | ⚠ game_id 待確認 |
| `sql_detective` | 霞光畫廊失竊案（SQL 偵探） | `sql_` | 已上線 | |
| `jlpt_mishitsu` | ⚠ 待補 | `jlpt_` | 已上線 | 目前無專屬事件；前綴保留，日後加專屬事件就用它 |
| `katsuyo_escape` | ⚠ 待補 | `katsuyo_` | 已上線 | |
| `swiftui_detective` | ⚠ 待補 | `swiftui_` | 已上線 | 專屬事件 `swiftui_hint_open`、`swiftui_solution_view` |
| `absolute_pitch` | 絕對音感養成所（en：Absolute Pitch Trainer／ja：絶対音感養成所） | `ap_` | 已上線 | 三語：/absolute-pitch/、/absolute-pitch/en/、/absolute-pitch/ja/；專屬事件 `ap_daily_goal`、`ap_pair_fixed`、`ap_progress_reset`；無聯盟 |
| `flower_shop` | ひより花店 | `flower_` | 已上線 | ⚠ 事件名稱待確認 |
| ⚠ `tozai_dojo` | 東西腔道場 | `tozai_` | 已上線 | ⚠ game_id 與事件待確認 |
| `shun_tabi` | 旬之旅（遊戲版） | — | 擱置 | 改做 season_booking（見工具表） |

---

## 故事／小說／追劇（content_group=story，id 參數 `work`）

`work` 直接用作品資料夾名（不含類別資料夾），**用連字號**（story 的例外，見 core §3-1 #2）。

| work | 類型 | 網址 | 前綴 | 狀態 | 備註 |
|---|---|---|---|---|---|
| `a-gentleman-in-moscow` | 小說分析 | story /books/a-gentleman-in-moscow/ | — | 規劃中 | Alison 製作；尚未上線，直接照 story.md 寫法建立 |
| `around-the-world-in-80-days-route` | 小說 | WP /around-the-world-in-80-days-route/ | — | 已上線 | 不搬；story 首頁外連 |
| `the-little-prince` | 小說分析 | story /books/the-little-prince/ | — | 規劃中 | |
| `pride-and-prejudice` | 小說分析 | story /books/pride-and-prejudice/ | — | 規劃中 | |
| `the-early-spring` | 追劇（原創，中／en／ja） | story /drama/the-early-spring/ | — | 待修 | Zoe；搬到 /drama/（舊網址留轉址頁）；改成不開自動廣告（不帶 `?client=`＋AdSense 後台網頁排除）；⚠ 追蹤寫法待核對 |
| `confession` | 追劇（原創） | story /drama/confession/ | — | 待修 | Zoe；搬到 /drama/（舊網址留轉址頁）；改成不開自動廣告（不帶 `?client=`＋AdSense 後台網頁排除）；⚠ 追蹤寫法待核對 |
| `when-i-meet-the-moon` | 追劇（原創，中／en／ja） | story /drama/when-i-meet-the-moon/ | — | 待修 | Zoe；搬到 /drama/（舊網址留轉址頁）；改成不開自動廣告（不帶 `?client=`＋AdSense 後台網頁排除）；⚠ 追蹤寫法待核對 |
| `hidden-love` | 追劇（原創） | story /drama/hidden-love/ | — | 待修 | Zoe；搬到 /drama/（舊網址留轉址頁）；改成不開自動廣告（不帶 `?client=`＋AdSense 後台網頁排除）；⚠ 追蹤寫法待核對 |
| `the-first-frost` | 追劇（原創，中／en／ja） | story /drama/the-first-frost/ | — | 待修 | Zoe；搬到 /drama/（舊網址留轉址頁）；改成不開自動廣告（不帶 `?client=`＋AdSense 後台網頁排除）；⚠ 追蹤寫法待核對 |
| `amidst-a-snowstorm-of-love` | 追劇 | story /drama/amidst-a-snowstorm-of-love/ | — | 待修 | Zoe；搬到 /drama/（舊網址留轉址頁）；改成不開自動廣告（不帶 `?client=`＋AdSense 後台網頁排除）；2026-10-04 補登記；⚠ 追蹤寫法待核對 |
| `lighter-and-princess` | 追劇 | story /drama/lighter-and-princess/ | — | 待修 | Zoe；搬到 /drama/（舊網址留轉址頁）；改成不開自動廣告（不帶 `?client=`＋AdSense 後台網頁排除）；2026-10-04 補登記；⚠ 追蹤寫法待核對 |

story 共用事件 `quiz_complete`、`progress_check` 不加前綴；追劇頁特有互動才登記前綴（例：`ep_`）。

---

## 待修清單（改版時處理，修完把狀態改回「已上線」並寫 CHANGELOG）

| 對象 | 問題 | 改成 |
|---|---|---|
| `trip_planner` | 沒送 `tool_id`；用 `affiliate_click`＋`platform`；用保留名稱 `tool`；share 的 `method=link` 不在值域 | `gtag('set')` 帶 tool_id；`cta_click`（cta_id＝位置、cta_type＝平台）；share method 改 native／copy_link |
| `jr_pass` | `affiliate_click`＋`platform`、`tool` 參數 | 同上 |
| 遊戲聯盟連結 | `cta_type=affiliate` | jlpt（trip_hall、trip_result、trip_article）→ `trip`；sql、katsuyo（below_game、room_clear、escape_room）、swiftui（dadaocheng_*、escape_room_*）→ `klook`。**改版日寫進 CHANGELOG**：之前的資料是 `affiliate`，看長期趨勢要合併 |
| 舊遊戲 | `rel="sponsored noopener"` 少 `nofollow`；沒有 `spec-version` meta | 補上 |
| 7 部追劇（5 部原創＋amidst-a-snowstorm-of-love、lighter-and-princess） | 開著自動廣告；沒有 spec-version；追蹤寫法未核對；網址還在第一層 | 搬到 /drama/、舊網址留轉址頁；不帶 `?client=`＋AdSense 後台網頁排除；補 spec-version；依 story.md 核對追蹤 |

（`trip_planner`、`jr_pass` 依 Project 裡 2026-09-22 的原始碼判斷，線上版本若已更新請改狀態。）
