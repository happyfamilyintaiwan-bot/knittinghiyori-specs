# games.knittinghiyori.com 規範

**版本：games-v1.8.1｜2026-10-10｜Zoe**（v1.8.1：主頁 NEW 只標最新三款；主頁 game_id 確認為 hub；主頁預覽圖 /assets/og-hub.png。v1.8：分享列加「加到我的最愛」按鈕（共用 /lib/hy-fav.js，事件 bookmark_shortcut）；篩選代碼 habit／sleep。v1.7：404 頁照 core v1.4，cta_id 改 notfound_card。v1.6.1：morse_code 進度圖卡。v1.6：共用引擎 /lib/hy-trainer/、篩選代碼 morse。v1.5：每款遊戲都可放少量主題相符的聯盟。v1.4.1：404 依語言切換。v1.4：分頁圖示換正式 logo、404 頁、主頁品牌列。v1.3.1：og 圖加品牌列。v1.3：結算畫面成績卡圖片。v1.2：頂端品牌列＋`brand_hub`；v1.2.1：品牌列換正式 logo。由各遊戲 README 整理，皆依《遊戲 GA4 v1.0》實作；原文未找到，標 ⚠ 處待 hyGame 程式碼或 DebugView 核對，核對後升 v1.1.1）
負責人：Zoe。先讀 `core.md`；本檔只寫 games 專屬的部分。

---

## 1. 網址與 repo

| 項目 | 規則 |
|---|---|
| repo | `happyfamilyintaiwan-bot/games`（GitHub Pages） |
| 網址 | `games.knittinghiyori.com/<slug>/`，資料夾＋`index.html`（＋og 圖 1200×630） |
| 分頁圖示 | 全部用正式 logo（方形「編織日和 Knitting Hiyori」，原檔 512px）做成 `/icons/` 整組：favicon.ico（16／32／48）、favicon-32、favicon-96、icon-192、icon-512、apple-touch-icon；**根目錄另放 `favicon.ico`、`apple-touch-icon.png`**（瀏覽器、Google、iPhone 書籤會直接找根目錄，沒有就顯示灰色地球）。換圖時連結加 `?v=N` 逼瀏覽器重抓 |
| 404 頁 | `404.html`，照 core §7：品牌列＋「4🌸4」＋一句說明（中英日，依網址 `/ja/`、`/en/` 或瀏覽器語言切換）＋主要按鈕「回遊戲主頁」（`notfound_hub`）＋次要按鈕「到編織日和主站」（`notfound_main`）＋推薦遊戲**最多 3 張**（`notfound_card`，帶 `game_id`）。卡片在瀏覽器讀遊戲主頁的 `a.card` 產生，有該語言版本的排前面；讀不到時用頁面裡寫死的 3 張備用。`noindex, follow`、不放 AdSense、有 GA4（page_title `遊戲\|404\|找不到頁面`）、頁尾 `.kh-legal` |
| 共用引擎 | `/lib/hy-trainer/`（實證訓練法系列共用：階段、門檻解鎖、交錯與間隔複習、進度紀錄）；內容包放各遊戲資料夾。改引擎前要確認所有使用中的遊戲都相容，存檔格式要能讀舊版 |
| og 圖 | 左上角品牌列：正式 logo（約 56px）＋「編織日和・小遊戲」（英：編織日和 · Games／日：編織日和・ミニゲーム），和頁面頂端品牌列一致；圖上網址寫到該遊戲（含語言）路徑，例 `games.knittinghiyori.com/absolute-pitch/en`。**換圖一律用新檔名**（`og-2.png`、`og-3.png`…，FB／LINE 才會重抓），og:image、twitter:image、JSON-LD 三處一起改；`og:image:alt` 開頭寫品牌名 |
| 多語 | 英日放在遊戲資料夾裡：`/<slug>/en/`、`/<slug>/ja/`（core §7 例外）；三語共用同一個 localStorage key；交付 zip 的最外層就是中文版 |
| slug／game_id | 資料夾用連字號、`game_id` 用底線，兩者對應（`jlpt-mishitsu` ↔ `jlpt_mishitsu`） |
| 品牌圖示 | `/icons/`（全站 favicon 以此為準，core §7） |
| 介紹文 | 每款遊戲在部落格有一篇 SEO 介紹文，英文代稱；遊戲頁與文章互連 |
| 工具型內容 | 放 tools 子網域，不放 games（例：季節訂房倒數 season_booking 由 Alison 直接在 tools 製作） |

開工前先在 `registry.md` 登記 `game_id` 與前綴。

---

## 2. 頁面結構（由上到下）

0. **編織日和品牌列**（頁面最上方）：正式 logo（方形「編織日和 Knitting Hiyori」，`/icons/logo-knitting-120.webp`，顯示 40px）＋「編織日和・小遊戲」（英：編織日和 · Games／日：編織日和・ミニゲーム），點了回遊戲主頁（`data-cta="brand_hub"`、`data-cta-type="game"`）；多語遊戲的語言切換放在同一列右側，400px 以下藏起「・小遊戲」（`.kh-brand-sub`）避免橫向溢出。寫法照 `_template/`（`.kh-brand-row`、`.kh-brand`），`max-width` 對齊該遊戲本體寬度；遊戲名放在品牌列下方
1. **遊戲**（首屏就是遊戲，不先放長說明）
2. 聯盟區（常駐，在遊戲區**外**）
3. 分享列：最後一顆是「加到我的最愛」（2026-10-10 起，遊戲主頁也有）。頁面結尾放一行 `<script src="/lib/hy-fav.js" defer></script>`，它會在每個「複製連結」按鈕後面自動補一顆，樣式跟著該遊戲的複製按鈕；英、日頁依 `<html lang>` 自動換字。瀏覽器不允許網頁自己加書籤，所以按下去是跳出「這台裝置怎麼加」的提示（App 內建瀏覽器、iPhone、Android、Mac、其他電腦各一種說明）。新遊戲的複製按鈕請用 `data-share="copy_link"`，才會自動補上
4. 回遊戲主頁大按鈕（`data-cta="about_hub"`、`data-cta-type="game"`，文案「探索更多互動遊戲 →」）
5. 廣告（1 個）
6. 頁尾 `.kh-legal`

- 聯盟連結只放遊戲區外、破關／結算畫面，**不放在作答中**。
- 存檔用 localStorage，key 寫在該遊戲 README；改版要相容舊存檔。

---

## 3. GA4

### 3-1 識別

| 項目 | 值 |
|---|---|
| 內容 id 參數 | `game_id` |
| `content_group` | `game` |
| `page_title` | `遊戲\|遊戲名稱\|學什麼`，例：`遊戲\|霞光畫廊失竊案\|SQL偵探入門`（`<title>`、og:title 不動） |

```js
gtag('set',{content_group:'game',game_id:'sql_detective',page_lang:'zh-Hant',page_title:'遊戲|霞光畫廊失竊案|SQL偵探入門'});
```

body 底部放標準 hyGame 追蹤碼：
- `HY_GAME_ID`＝game_id
- `HY_GAME_ROOT`＝遊戲區的選擇器（**不含**聯盟區與分享列），例：`'#app'`、`'#stage, #finale'`
- `HY_GAME_LANG`＝回傳 `zh`／`en`／`ja`（多語遊戲每頁不同）；頁首語言切換送 `lang_switch`（`source=header`、`from_lang`＝目前 page_lang）

### 3-2 遊戲共用事件（hyGame）

| 事件 | 何時 | 參數 |
|---|---|---|
| `game_start` | 開始玩 ⚠ 確切觸發點以 hyGame 為準 | `entry_point`（direct／shared／saved） |
| `round_start` | 一局開始 | `option`、`level` |
| `round_end` | 一局結束 | `option`、`level`、`result`（complete／fail／quit）、`item_count`、`correct_count`、（選用）`score` |
| `game_exit` | 離開頁面 | |
| `game_unlock` | 解鎖 | 值如 `escape_l01`、`escape_all`、`key_<章節>`、`note_c`、`all_notes` ⚠ 參數名待核 |
| `game_milestone` | 累積作答第 1／10／50／100 題（可延伸） | `milestone` |
| `tutorial_begin`／`tutorial_complete` | 教學開始／完成（每次載入各一次） | |
| `game_settings` | 改設定 | 值如 `sound_on`、`noise_off`、`timbre_<音色>` |
| `bookmark_shortcut` | 按「加到我的最愛」（core §3-2 共用事件；由 /lib/hy-fav.js 送出，不算 `game_start`） | `option`＝提示的裝置：inapp／ios／android／mac／desktop；遊戲主頁 `game_id=hub` |
| `share`、`cta_click` | 照 core §3-2 | 分享 `content_type`：破關前 `game`、破關後 `result` |

### 3-3 一局怎麼定義

- 每款在 README 寫明「一局＝什麼」（一關、一間密室、一次訓練）。
- 切換關卡、回地圖、離開頁面 → 送 `result=quit`。
- `option`：小寫英文，表示模式或案件（`case01`、`escape`、`train`／`test`／`review`、`clue`／`door`／`blitz`）。
- `level`：`l` ＋兩位數（`l00`–`l99`）。
- `item_count`＝這局作答數；`correct_count`＝答對數（或「一次答對」1／0，README 寫明）。
- `score` 只在有意義時送（例：驗收正確率），否則不送。

### 3-4 專屬事件

- 格式 `{前綴}_{動詞}`，前綴先到 `registry.md` 登記；盡量帶 `option`、`level`。
- 常見：`{前綴}_hint_open`、`{前綴}_solution_view`。
- 專屬參數（如 `streak`、`pair`）不註冊；要進報表時，先查 core §3-4 能否沿用。

### 3-5 CTA 值

| 位置 | cta_id | cta_type |
|---|---|---|
| 頂端品牌列（每頁必有，含遊戲主頁、404） | `brand_hub` | game |
| 404 頁：回遊戲主頁 | `notfound_hub` | game |
| 404 頁：到主站 | `notfound_main` | game |
| 404 頁：推薦遊戲卡片（帶 `game_id`；2026-10-10 前是 `notfound_game`） | `notfound_card` | game |
| 回遊戲主頁（每頁必有） | `about_hub` | game |
| 主頁、遊戲頁尾：到主站（部落格） | `blog_banner`（主頁橫幅）、`footer_main`（頁尾） | article |
| 遊戲頁尾：回遊戲主頁（小連結） | `footer_hub` | game |
| 連到介紹文 | `about_article` | article |
| 連到規則依據文章 | `source_article` | article |
| 參考文獻、資料來源 | `source_link`（或 `source_*`） | other |
| 聯盟（遊戲頁） | 位置名：`below_game`、`room_clear`、`trip_result`… | **平台名**（trip、klook…） |
| 介紹文：開始玩 | `intro_play`、`body_play`、`end_play` | game |
| 介紹文：其他遊戲 | `related_game` | game |
| 介紹文：聯盟 | 位置或主題名：`escape_room`、`trip_article`… | 平台名 |

分享網址帶 `?ref=share` → `game_start` 的 `entry_point=shared`；已有存檔的玩家 → `saved`。

### 3-6 GA4 後台

- 參數：`game_id`、`level`、`correct_count`、`milestone` ⚠ 以 GA4 Custom definitions 匯出表核對註冊狀態
- 重要事件 ⚠ 待定（core §3-4）
- 不另建資源

---

## 4. AdSense

| 項目 | 規則 |
|---|---|
| slot | `5316670118` |
| 數量 | 每頁 1 個 |
| 位置 | 回主頁大按鈕下方；用 `.kh-ad--game`（上方 150px），不貼近遊戲區與作答按鈕 |
| 載入碼 | 不帶 `?client=`；所有 `<a>` 加 `data-google-vignette="false"` |

---

## 5. 聯盟

- games Drive 放 head 第一個 script（core §1）。
- 手動連結 `rel="sponsored nofollow noopener"` ＋揭露文字（舊遊戲為 `sponsored noopener`，改版時補 `nofollow`，見 registry 待修清單）。
- 連結集中在設定物件（`LINKS`／`AFF`），找不到時按鈕自動隱藏。
- **每款遊戲都可以放 AdSense 與 Travelpayouts／聯盟，但要少量、不影響玩**：聯盟每頁最多 1～2 個位置，放遊戲區外；主題和旅遊無關時，找主題相符的商品（例：絕對音感中文頁放蝦皮「練習用耳機」，`cta_id=below_game`、`cta_type=shopee`）。
- 蝦皮只放中文頁；英日頁用 Klook 或不放。
- 聯盟網址放進 HTML 時，和號寫成 `&amp;`；能用聯盟後台的短網址（`s.shopee.tw/…`）就用短網址。
- 演唱會、音樂會票券只連官方。

---

## 6. 版型

- 白底黑字，**每款遊戲自訂一個強調色與字體**，不共用 tools 色票。
- 回主頁大按鈕用該遊戲強調色，醒目。
- Google Fonts 拆成多個 `<link>`（每個字體一個），避免網址出現和號（core §3-1 #7）；網址參數用 `String.fromCharCode(38)`。
- 視覺檢查：Playwright 截圖 390／1280 × 新玩家、遊戲中、結算畫面。

---

### 6-1 成績卡圖片（結算畫面，2026-10-04 起；已套用：absolute_pitch（12 音驗收成績卡）、morse_code（進度圖卡：已點亮 N／41 盞燈，點亮 3 盞後開放，入口在交班畫面與守燈日誌））

玩家完成一局／驗收後，結果區放「做成績卡圖片」按鈕，在瀏覽器用 canvas 畫圖，不經伺服器。

| 項目 | 規定 |
|---|---|
| 尺寸 | 1080×1350（4:5 直式，IG／Threads／X 不裁切） |
| 內容 | 遊戲名＋日期、主要成績大字（例：正確率）、一句依成績分級的短評、2～3 個輔助數字、細項圖（例：各音正確率）；不放玩家姓名或任何個資 |
| 品牌 | 中央一個大而淡的斜放浮水印（「編織日和」＋`games.knittinghiyori.com`，透明度約 8%，英文頁用 Knitting Hiyori，字太長自動縮小）＋底部金色品牌列（正式 logo `/icons/logo-knitting-240.webp`、品牌名、**該語言的遊戲網址**、「免費玩 →」） |
| 按鈕 | 手機支援分享檔案時「分享圖片」（`navigator.share` 帶圖＋分享文字＋`?ref=share` 網址）；一律有「下載圖片」與「複製連結」（很多 App 分享圖片時會丟掉文字，網址要靠玩家貼上才點得到） |
| 追蹤 | 分享圖片 `share {method:native, content_type:result}`；取消 `share_cancel`；下載 `export {method:image, content_type:result}`；複製連結 `share {method:copy_link, content_type:result}` |
| 字型 | 先 `document.fonts.load(字型, 卡上文字)`，最多等 1.5 秒，沒載完的字用系統字型補（中文 Google Fonts 分片第一次載入可能要數秒） |
| 檔案 | JPEG 品質 0.92（PNG 編碼 1080×1350 要 1～2 秒；社群會再壓縮），檔名 `<slug>-YYYY-MM-DD.jpg` |
| 驗收 | 中英日各產生一張檢查排版；手機實機按「分享圖片」確認分享選單出現；390 寬無橫向溢出 |

---

## 7. 主頁交接（新遊戲上線時）

遊戲主頁加卡片，交接內容：

| 欄位 | 說明 |
|---|---|
| 名稱、網址、一句介紹 | 一句介紹寫「學什麼＋怎麼玩」 |
| `data-game` | game_id |
| `data-cta-type` | `game` |
| `data-topic`／`data-skill` | 沿用 `HY_FILTERS` 既有代碼；新代碼同步加進 HY_FILTERS |
| NEW 標記 | **只標最新上線的三款**（2026-10-10 Zoe 決定）。新遊戲上線時：新卡片加 NEW，同時把第四新那款的 NEW 拿掉 |
| 主頁預覽圖 | `/assets/og-hub.png`（1200×630，右邊是最新 6 款的縮圖）。新遊戲上線後重做一次，FB 偵錯工具重抓 |
| JSON-LD 遊戲清單 | name、url、description、inLanguage |
| 404 多語卡片 | 有英日版的遊戲：在 `404.html` 的 `LANG_GAMES` 加一筆（各語言 url、name、desc）；只有中文的遊戲不用改 404 |
| 介紹文網址 | 文章發布後回填 |

既有篩選代碼：

| topic | skill | 遊戲 |
|---|---|---|
| japanese | vocab | jlpt_mishitsu、flower_shop ⚠ |
| japanese | conjugation | katsuyo_escape |
| coding | sql | sql_detective |
| coding | swiftui | swiftui_detective |
| music | ear_training | absolute_pitch |
| morse | ear_training、listening | morse_code |
| habit | sleep | sleep_rhythm |
| travel | planning | shun_tabi（擱置） |

---

## 8. 驗收

core §9 全部，再加：

- `?hy_debug=1` 玩一輪：完成一局 → 開下一局後中途離開 → 點聯盟 → 點回主頁 → 關分頁。DebugView 依序：`game_start → round_start → round_end(complete) → round_start → round_end(quit) → cta_click → cta_click(about_hub) → game_exit`（有教學的遊戲前面加 `tutorial_begin`／`tutorial_complete`）
- GA4 報表頁面標題為 `遊戲|…|…`
- LINE／FB 分享預覽標題與 og 圖正確；從分享連結進入 `entry_point=shared`
- Console 印出 `[hy-game]`

---

## 9. 部署

1. 在 `registry.md` 登記 game_id 與前綴。
2. 本機測，跑 §8。
3. GitHub games repo → Upload files → 拖入整個資料夾 → Commit（更新同樣上傳，覆蓋舊檔）。
4. **已加過廣告碼的遊戲**：新版要和線上版的廣告碼合併後再上傳，不可直接覆蓋。
5. 等 1–3 分鐘，`?hy_debug=1` 驗收。
6. 主頁交接（§7）、sitemap 加一筆、GSC 要求建立索引。
7. 介紹文：WordPress「自訂 HTML」區塊貼上（data-cta 才不會被濾掉）。
8. Travelpayouts 後台確認 Drive。

---

## 10. 待補

- 以《遊戲 GA4 v1.0》原文或 hyGame 程式碼核對 §3-2 的觸發點與參數名
- ~~遊戲主頁的 game_id~~（2026-10-10 確認：`hub`，專屬事件 `hub_filter`）
- flower_shop、東西腔道場的事件寫法（DebugView）
- 遊戲重要事件
- 成績卡套到其他遊戲（absolute_pitch 試點上線後看 `export`／`share content_type=result` 數據再排）
