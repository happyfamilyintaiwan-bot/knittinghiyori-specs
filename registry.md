# 內容 ID 與事件前綴登記表（registry）

**版本：registry-v1.3.10｜2026-10-10｜Zoe＋Alison**（v1.3.10：待修清單 404 cta_id 劃掉 poem。v1.3.9：hub 的 game_id 確認。v1.3.8：swiftui_detective、tozai_dojo、flower_shop 補中文名、值域與聯盟。v1.3.7：新增 sleep_rhythm。v1.3.6：sql_detective 補專屬事件、聯盟與介紹文。v1.3.5：jlpt_mishitsu 補中文名與聯盟。v1.3.4：待修清單加 404 cta_id 統一。v1.3.3：品牌列待修移除 poem。v1.3.2：katsuyo_escape 補中文名與聯盟。v1.3.1：新增 hiyori_pet。v1.3：新增 morse_code。v1.2：新增學習筆記 study 區）

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
| `hub` | 遊戲主頁 | `hub_` | 已上線 | game_id 已確認；專屬事件 `hub_filter`（option＝篩選代碼、source＝topic／skill）；卡片點擊 `game_card`（帶 option＝該遊戲 game_id、card_index）；到主站 `blog_banner`、`footer_main`（article，2026-10-10 起；之前是 `mainsite`，頁尾之前叫 `footer`） |
| `sql_detective` | 霞光畫廊失竊案（SQL 偵探） | `sql_` | 已上線 | 只有中文；level＝l00–l07（關卡）；option＝case01；一局＝一個還沒破解的關卡；專屬事件 `sql_hint_open`、`sql_solution_view`；聯盟 `below_game`（klook，2026-10-10 起；之前是 affiliate）；介紹文 knittinghiyori.com/sql-beginner-game/（文中 `escape_room` 仍是 affiliate，待 WordPress 改） |
| `jlpt_mishitsu` | JLPT 單字密室（言の葉館） | `jlpt_` | 已上線 | 目前無專屬事件；前綴保留，日後加專屬事件就用它；level＝l01–l05（密室）；option＝clue 等；聯盟 `trip_hall`、`trip_result`（trip，2026-10-10 起；之前是 affiliate）；介紹文 knittinghiyori.com/jlpt-vocab-game/（文中 `trip_article` 待 WordPress 改） |
| `katsuyo_escape` | 活用館脫出（活用館からの脱出） | `katsuyo_` | 已上線 | 專屬事件 `katsuyo_tutorial_skip`、`katsuyo_hint_open`；聯盟 `below_game`、`room_clear`（klook，2026-10-09 起；之前是 affiliate）；介紹文 knittinghiyori.com/japanese-verb-conjugation-game/（文中 `escape_room` 仍是 affiliate，待 WordPress 改） |
| `swiftui_detective` | 雨夜懷錶案（SwiftUI 偵探） | `swiftui_` | 已上線 | 只有中文；level＝l00–l07（章節）、l08（結案指認）；option＝case01；專屬事件 `swiftui_hint_open`、`swiftui_solution_view`；聯盟只在結案畫面：`dadaocheng_result`、`escape_room_result`（klook，2026-10-10 起；之前是 affiliate）；存檔 localStorage swiftui-noir-v2；介紹文 knittinghiyori.com/swiftui-tutorial-detective-game/ |
| `absolute_pitch` | 絕對音感養成所（en：Absolute Pitch Trainer／ja：絶対音感養成所） | `ap_` | 已上線 | 三語：/absolute-pitch/、/absolute-pitch/en/、/absolute-pitch/ja/；專屬事件 `ap_daily_goal`、`ap_pair_fixed`、`ap_progress_reset`；聯盟：中文頁蝦皮練習用耳機（`below_game`／shopee，2026-10-04 起）；介紹文 knittinghiyori.com/absolute-pitch-training-game/（2026-10-04 發布） |
| `flower_shop` | ひより花店 | `flower_` | 已上線 | 只有中文；目前無專屬事件（前綴保留）；option＝kana／flower_quiz／hana_quiz／typing_hana／typing_<語言>；level＝relaxed／standard／challenge／review（測驗）、small／medium／large＋_<計時模式>（打字）；聯盟 `flower_trip`（klook，2026-10-10 起；之前是 affiliate），cta_click 另帶 option＝花的英文名（2026-10-10 前沒送到）；頁尾 `footer_hub`（game）、`footer_main`（article）（之前都是 `footer`，到主站那個之前 cta_type 是 `mainsite`）；介紹文連結 `about_article`（之前是 `article_link`）；介紹文 knittinghiyori.com/japanese-kana-game/ |
| `morse_code` | 守燈人摩斯日誌 | `morse_` | 已上線 | 實證訓練法系列第 1 款；只有中文；共用引擎 /lib/hy-trainer/；level＝Koch 課數 l01–l40；option＝koch／group；專屬事件 morse_skip_intro、morse_daily_goal（streak）、morse_pair_play、morse_progress_reset；聯盟 cta_id=lighthouse_trip（klook）、gear_card（shopee，AirPods，2026-10-09 起）；2026-10-09 上線；介紹文 knittinghiyori.com/morse-code-training-game/（2026-10-09 發布） |
| `sleep_rhythm` | 固定作息燈塔 | `sleep_` | 已上線 | 規律作息養成；只有中文；一局＝一次打卡（option=wake／sleep，level＝燈靈階段 l01–l06）；不送打卡時間、差距、準不準時或城市；專屬事件 sleep_skip_intro、sleep_backfill、sleep_morning_light、sleep_report_open、sleep_fleet_open、sleep_diary_open、sleep_diary_answer（option＝手記頁 id）、sleep_signal_send（option=gm／gn／tg／ch）、sleep_friend_add（result=new／update、source=link／paste）、sleep_progress_reset；game_unlock 含 spirit_l02–l06、diary_d01–d21、diary_d30–d100（每 10 天）、diary_f01／f03／f05／f10（聯盟的信）；邀請朋友 share content_type=invite；邀請資料放網址 #f= 片段，GA4 載入前移除；聯盟 cta_id=lighthouse_trip（klook）；存檔 localStorage hy_sleep_v1；2026-10-10 上線；介紹文 knittinghiyori.com/sleep-schedule-habit-game/ |
| `hiyori_pet` | 日和毛孩（網頁電子寵物） | `pet_` | 規劃中 | 網址 /hiyori-pet/，預定 2026-11-09 上線，施工分支 `hiyori-pet`；只有中文；專屬事件 `pet_adopt`、`pet_action`、`pet_stage`、`pet_mail_read`、`pet_pip_open`、`pet_pwa_install`、`pet_move`（option＝export／import）；`pet_walk_remind`（option＝notice／block）、`pet_walk_done`（option＝manual／idle）、`pet_walk_snooze`（option＝later／today）；開發中再加 `pet_visit_share`／`pet_visit_open`（串門子連結）；聯盟 klook（cta_id `trip_result`）；localStorage `hiyori-pet:save`、`hiyori-pet:book`、`hiyori-pet:ios-tip` |
| `tozai_dojo` | 東西腔道場 | `tozai_` | 已上線 | 只有中文；game_id 已確認；目前無專屬事件（前綴保留）；一局＝一回 10 題，option＝mixed，沒有 level；round_end 帶 score；聯盟 `start_card`、`result_card`（trip，2026-10-10 起；之前是 affiliate）；分享網址 `?ref=share`（之前是 `?via=share`，舊連結仍認；2026-10-10 前 entry_point=shared 沒記到）；存檔 localStorage tozai-best2；介紹文尚未寫 |
| `shun_tabi` | 旬之旅（遊戲版） | — | 擱置 | 改做 season_booking（見工具表） |

---

## 故事／小說／追劇（content_group=story，id 參數 `work`）

`work` 直接用作品資料夾名（不含類別資料夾），**用連字號**（story 的例外，見 core §3-1 #2）。

| work | 類型 | 網址 | 前綴 | 狀態 | 備註 |
|---|---|---|---|---|---|
| `a-gentleman-in-moscow` | 小說分析 | story /books/a-gentleman-in-moscow/ | — | 已上線 | Alison；2026-10-04 上線（story `d02d488`），GSC 已送索引；用 hy-story.js＋story.md §3 小說事件；⚠ GA4 DebugView 待 Alison 核對 |
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

## 學習筆記（content_group=study，id 參數 `topic`）

`topic` 直接用主題資料夾名，**用連字號**（同 story 的例外）。首頁主題卡目前直接連各主題的部落格主力文章（`topics.json` 的 `blog`），筆記上線後再改回主題頁。

| topic | 名稱 | 網址 | 狀態 | 備註 |
|---|---|---|---|---|
| `hub` | 學習筆記首頁 | study / | 已上線 | |
| `cs50` | 哈佛 CS50 計算機科學概論 | study /cs50/ | 已上線 | 公開課；卡片連 `/harvard-cs50-courses/` |
| `claude-ai` | Claude AI 與 AI 分身 | study /claude-ai/ | 已上線 | 自學；卡片連 `/claude-beginner-guide-anthropic-academy-courses/` |
| `minerva-mda` | Minerva MDA | study /minerva-mda/ | 已上線 | 上過的課；卡片連 `/minerva-university-mda-master-degree-guide/`；⚠ 正式課程名稱待 Alison 補 |
| `japanese` | 日文學習 | study /japanese/ | 已上線 | 自學；卡片連 `/japanese-verb-conjugation-six-forms-five-types/` |
| `chess` | 西洋棋 | study /chess/ | 已上線 | 自學；卡片連 `/chess-for-beginners/` |

## 待修清單（改版時處理，修完把狀態改回「已上線」並寫 CHANGELOG）

| 對象 | 問題 | 改成 |
|---|---|---|
| `trip_planner` | 沒送 `tool_id`；用 `affiliate_click`＋`platform`；用保留名稱 `tool`；share 的 `method=link` 不在值域 | `gtag('set')` 帶 tool_id；`cta_click`（cta_id＝位置、cta_type＝平台）；share method 改 native／copy_link |
| `jr_pass` | `affiliate_click`＋`platform`、`tool` 參數 | 同上 |
| 遊戲聯盟連結 | `cta_type=affiliate` | jlpt（~~trip_hall、trip_result~~ 2026-10-10 遊戲頁已改；trip_article 在 WordPress 介紹文，待改）→ `trip`；sql（~~below_game~~ 2026-10-10 遊戲頁已改；escape_room 在 WordPress 介紹文，待改）、katsuyo（~~below_game、room_clear~~ 2026-10-09 遊戲頁已改；escape_room 在 WordPress 介紹文，待改）、swiftui（~~dadaocheng_result、escape_room_result~~ 2026-10-10 遊戲頁已改）→ `klook`；tozai（~~start_card、result_card~~）→ `trip`、flower（~~flower_trip~~）→ `klook`，都在 2026-10-10 改完。**遊戲頁全部改完，只剩 WordPress 介紹文裡的**。**改版日寫進 CHANGELOG**：之前的資料是 `affiliate`，看長期趨勢要合併 |
| 舊遊戲 | `rel="sponsored noopener"` 少 `nofollow`；沒有 `spec-version` meta | 補上 |
| 404 頁 cta_id（~~games~~、~~poem~~ 2026-10-10 已改、study） | ~~games `notfound_game`~~；study `notfound_topic`；~~poem `notfound_home`、`notfound_poem`~~，和 core §7 統一值不同 | games、study `→ notfound_card`；~~poem `notfound_home → notfound_hub`、`notfound_poem → notfound_card`~~（poem#8）；同步改站別檔 CTA 表；改版日寫進 CHANGELOG，GA4 長期趨勢要合併舊值 |
| story 首頁與作品頁、tools 既有頁面（games、poem 已完成） | 頁首最上方沒有品牌列 | 依 core §7「頁首品牌列」補上；各負責人改自己範圍的頁面，story 首頁 hub 兩人共管 |
| 7 部追劇（5 部原創＋amidst-a-snowstorm-of-love、lighter-and-princess） | 4 部 8 頁仍用舊的內嵌追蹤（已改送 content_group=story、work）；page_title 不是 `追劇\|…` 格式 | 改用 hy-story.js、page_title 改成 story.md 格式，重驗 DebugView（搬資料夾、關自動廣告、spec-version 已於 2026-10-04 完成） |

（`trip_planner`、`jr_pass` 依 Project 裡 2026-09-22 的原始碼判斷，線上版本若已更新請改狀態。）
