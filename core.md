# knittinghiyori 共用規範（core）

**版本：core-v1.3｜2026-10-04｜Zoe＋Alison**（v1.3：新增 study 子網域、cta_type 加 study；分工改為 Alison 只交內容、上架全部由 Zoe 處理。v1.2：cta_type 加 story、頁尾聯盟文字不限旅遊、§7 新增頁首品牌列。v1.1：新增負責分工、story 自動廣告範圍、games 多語網址例外。標 ⚠ 處待以 GA4 Custom definitions 匯出表或 DebugView 核對，核對後升 v1.1.1）

適用：部落格（knittinghiyori.com）與 tools／games／story／poem／study 五個子網域。
各站的差異寫在 `tools.md`／`games.md`／`story.md`／`poem.md`／`study.md`／`blog.md`。**core 與各站檔案衝突時，以 core 為準**；各站需要例外時，先改 core 說明例外，不要在各站檔案自行推翻。

---

## 0. AI 使用規則

- 開工前先讀本檔＋對應站別檔案，第一句回報兩個檔案的版本號，以及 `CHANGELOG.md` 最新一筆的日期與內容。
- 讀不到檔案時直接說讀不到，**不可以憑記憶或舊副本工作**。
- 對話中若決定修改規範，結束前輸出：要改的檔案段落（可直接貼上）＋一筆 CHANGELOG 條目。
- 每個頁面 `<head>` 放 `<meta name="spec-version" content="core-v1.2/tools-v2.2.1">`（換成實際版本）。

### 負責分工（2026-10-04 起）
| 範圍 | 內容負責人 | 規範檔 |
|---|---|---|
| tools 子網域（含還沒搬家的 WordPress 工具） | Alison | tools.md |
| story：小說（novel） | Alison | story.md |
| story：追劇（drama）、漫畫（comics），含 5 部原創追劇 | Zoe | story.md |
| study 子網域（學習筆記） | Alison | study.md |
| games 子網域 | Zoe | games.md |
| poem 子網域 | Zoe | poem.md |
| 部落格文章 | 兩人 | blog.md |
| core.md、registry.md、story 首頁 hub 外框、story.md 共用段落 | 兩人共管 | — |
| 上架：repo、分支、PR、build、驗收、合併、發布、DNS／GA4／GSC／AdSense 後台、本規範 repo | Zoe | — |

```
Alison（claude.ai chat）── 交 4 項 ──→ Zoe 的 Claude Code
  決定寫什麼、寫成怎樣                 檢查規範、build、驗收、PR、合併、發布
```

- **內容負責人**決定寫什麼、寫成怎樣；**上架全部由 Zoe 的 Claude Code 處理**（所有子網域）。Alison 不碰 repo、分支、PR。
- **Alison 交件 4 項**（在 claude.ai 寫好交給 Zoe）：① 放哪（站、主題／作品，例：study／cs50）② 完整內容（Markdown）③ 英文網址（例：`week-0-scratch`）④ 特別要求（聯盟連結、圖片、要不要上首頁）。缺項時先問，不要猜。
- **上架不改意思**：上架 Alison 的內容時，只修格式、規範、錯字與技術問題；要改文字的意思、觀點或結構，先問 Alison。
- **不越界**：AI 發現這次工作會改到另一位負責的「內容」（不是上架動作）時，先停下來提醒，確認要不要繼續。
- **放錯位置要轉移**：內容依類型歸負責人，不依放在哪個 repo。放錯子網域或 repo 的內容要提出來，由負責人決定放哪。
- **存檔流程**：Zoe 的 AI 從最新的 main 開 `zoe/<主題>` 分支，`build` 0 問題、驗收後開 PR，squash 合併（有保護的 main 一律走 PR）。內容來自 Alison 時，合併訊息開頭寫「Alison:」，之後查得到是誰的內容。
- **舊流程收尾**：v1.3 之前已開的 `alison/<主題>` PR 照舊由 Zoe 檢查越界、衝突並驗收後合併；不再開新的。
- **確認身份**：Zoe 的桌機預設是 Zoe。開始改任何 repo 前先 `git pull`。
- 負責人可以直接決定自己範圍的規範，並寫 CHANGELOG；共管的部分要對方確認。

### 版本號規則
- **中版號**（v1.0→v1.1）：影響追蹤數據或上線頁面的改動，例：事件名稱、參數、page_title 格式、廣告位置、固定值。
- **小版號**（v1.0→v1.0.1）：文字修正、補充說明、不影響已上線頁面。

---

## 1. 固定值

| 項目 | 值 |
|---|---|
| GA4 評估 ID（全站共用一個資源） | `G-ZQZHTYTRMQ` |
| AdSense 發布商 ID | `ca-pub-2022028565680247` |
| ads.txt | 主站根目錄，子網域沿用，不另外放 |
| 隱私權政策 | `https://knittinghiyori.com/privacy-policy/`（各子網域頁尾都連到這裡） |
| GitHub 帳號 | `happyfamilyintaiwan-bot`，**Zoe 與 Alison 共用同一個帳號**：GitHub 分不出是誰，靠分支名 `alison/<主題>` 與合併訊息開頭「Alison:」區分。Zoe 桌機 clone 在 `~/Sites/knittinghiyori/`；tools 的 main 設保護，只能經 PR 合併 |

### 各子網域的值（不可混用，混用報表會分不出收益來源）

| 子網域 | AdSense slot | Travelpayouts Drive | 自動廣告 |
|---|---|---|---|
| tools | `3114811513` | `emrld.ltd/NTc5OTI2.js?t=579926` | 不開 |
| games | `5316670118` | `emrld.ltd/NTc4NjIz.js?t=578623` | 不開 |
| poem | `6629751780` | `emrld.ltd/NTc4NjIw.js?t=578620` | 不開 |
| story | `2285424505` | `emrld.ltd/NTc4NjI0.js?t=578624` | 首頁開；小說、追劇、漫畫頁（含 5 部原創追劇）**不開**（不帶 `?client=`＋AdSense 後台網頁排除，見 story.md） |
| study | ⚠ 待建立 | ⚠ 待建立 | 不開 |

---

## 2. `<head>` 順序（子網域）

1. Travelpayouts Drive（精簡版，保留 `data-cfasync="false"`；WordPress 外掛用的屬性不用帶）
2. meta charset／viewport、title、description、canonical、hreflang、OG、favicon、字體
3. AdSense 載入碼（不開自動廣告的站：**不帶 `?client=`**）
4. GA4：`gtag('set', {content_group, <內容>_id, page_lang, page_title})` 後再 `config`
5. JSON-LD
6. `spec-version` meta

---

## 3. GA4 統一追蹤

> 本節合併《工具 v1.2》《遊戲 v1.0》《故事 v1.5》。合併定版後，三份舊規範只作為歷史紀錄。⚠ 待 Alison 以 v1.2／v1.0 原文核對。

### 3-1 設計原則
1. 一個參數名稱＝一種意思，全站通用。
2. 內容 id 各用各的：工具 `tool_id`、遊戲 `game_id`、故事／小說／追劇 `work`，不互相借用。工具與遊戲的 id 用**底線**（`travel_split`）；**story 的 `work` 例外用連字號**，直接等於作品資料夾名（`a-gentleman-in-moscow`），不要改成底線。**study 的 `topic` 同樣用連字號**，直接等於主題資料夾名（`claude-ai`）。工具若放在 games 子網域，仍送 `tool_id`。
3. `content_group`：工具＝`tool`、遊戲＝`game`、故事＝`story`（⚠ 待核對既有作品）、學習筆記＝`study`、詩＝⚠ 待確認。
4. **參數值只能是固定的英文代碼**：不送讀者輸入的文字、中文句子或個資。
5. 不逐次送高頻動作（按鍵、輸入），結果彙總在一個事件。
6. 名稱 40 字元內；參數值 100 字元內；每事件 25 個參數內。
7. **追蹤碼不出現「和號」字元**，註解只用 `/* */`（需要時寫 `\x26`）。WordPress 上一定會壞，子網域也維持同一寫法。
8. `track()` 包 try/catch；GA4 沒載入時先排進 dataLayer。追蹤壞掉不能弄壞功能。
9. 網址加 `?hy_debug=1` 時送 `debug_mode`，Console 印出 `[hy-tool]`／`[hy-game]`。
10. `page_title` 格式：`類別|名稱|做什麼`（半形 `|`、不空格），例：`工具|旅費分帳計算機|出國多幣別分帳`。英日版用同一個，靠 `page_lang` 區分。

### 3-2 共用事件

| 事件 | 何時觸發 | 主要參數 |
|---|---|---|
| `cta_click` | 點任何 `[data-cta]` | `cta_id`（位置）、`cta_type`（去哪裡）、`link_url`、（總覽頁）`option`、`card_index` |
| `share`／`share_cancel` | 傳給別人 | `method`、`content_type` |
| `export` | 自己留存 | `method`（copy_text／image／print） |
| `faq_open` | 展開 FAQ | `option` |
| `lang_switch`／`lang_auto` | 切換語言 | `source`、`from_lang` |
| `open_saved_shortcut`、`install_*`、`pwa_*`、`bookmark_shortcut` | 加到桌面相關 | `option`／`result` |

- `share` 和 `export` 的分法：傳給別人 → `share`；自己留存 → `export`。
- 聯盟點擊一律用 `cta_click`，**不再使用 `affiliate_click`**。
- **`cta_id` 記位置**（各站自訂，例：tools 推薦卡 `rec_card`、遊戲 `below_game`／`room_clear`、小說 `buy_book`），一頁有多個聯盟位置時靠它比較哪個位置有效。
- **`cta_type` 記去哪裡，聯盟一律填平台名**（trip、agoda、booking、klook、kkday、shopee…）；只有平台不明時才用 `affiliate`。要看「全部聯盟點擊」，用「`cta_type` 屬於平台清單」篩，不用 `cta_id`。不另開平台參數（`platform` 是保留名稱，也會多佔一個自訂維度）。新平台先加進 3-3 值域。
- CTA 寫法：`data-cta="rec_card" data-cta-type="klook"`。
- 各站自己的事件（如工具的 `tool_start`／`tool_result`、遊戲的開始／結束事件）寫在各站檔案。

### 3-3 值域

| 參數 | 允許的值 |
|---|---|
| `method`（share） | native、line、facebook、threads、x、telegram、copy_link、copy_text |
| `content_type` | result、tool、game、story（⚠ 詩待補） |
| `cta_type` | tool、article、game、story、study、trip、agoda、booking、klook、kkday、shopee、affiliate、other |
| `entry_point` | direct、shared、saved |
| `page_lang` | zh-Hant、en、ja |

### 3-4 參數字典

| 參數 | 意思 | 註冊來源 |
|---|---|---|
| `tool_id` | 哪個工具 | 工具規範 |
| `work` | 哪部作品（story） | ⚠ 待註冊（story.md §3-3） |
| `topic` | 哪個學習主題（study） | ⚠ 待註冊（study.md §3） |
| `page_lang` | 介面語言 | 故事規範 |
| `cta_id`、`cta_type` | 點的位置、去哪裡 | 故事規範 |
| `entry_point` | 從哪裡開始用 | 故事規範 |
| `method`、`content_type`、`option`、`source`、`result` | 見 3-2、3-3 | 工具規範 |
| `item_count`（指標） | 個數 | 工具規範 |
| `duration_sec`（指標） | 秒數 | 故事規範 |
| `game_id` | 哪個遊戲 | 遊戲規範 |
| `level`、`correct_count`、`milestone` | 關卡（l00–l99）、答對數、里程碑 | ⚠ 遊戲規範（以 GA4 匯出表核對） |
| `card_index`、`score`、`pct` | 數字 | 不註冊（需要時再加） |

- 自訂維度名額（事件範圍 50 個）**全站共用**，新增參數前先查這張表，能沿用就沿用。
- 保留名稱（不要使用）：`lang`、`tool`、`type`、`device`、`platform`、`content`、`choice`、`outcome`、`level_name`、`success`、`character`。
- 重要事件：`share`、`cta_click`、`tool_result`、`open_saved_shortcut`（⚠ 遊戲的待補）。
- 子網域都在 knittinghiyori.com 底下，cookie 共用，**不用設定跨網域**。

### 3-5 內容 ID 與前綴登記

- 全部登記在 `registry.md`（工具、遊戲共用一張表），前綴不可重複。
- 新工具／遊戲開工前先登記，再開始寫程式。

---

## 4. AdSense 共用規則

| 項目 | 做法 |
|---|---|
| 不開自動廣告的站 | 載入碼不帶 `?client=`；所有 `<a>`（含 JS 產生的）加 `data-google-vignette="false"` |
| 位置 | 不放在輸入區、結果區、按鈕、遊戲畫面附近，上下至少留 150px |
| 標示 | 版位上方「廣告／Advertisement／広告」小標 |
| 沒填滿 | 整塊隱藏（`.kh-ad ins[data-ad-status="unfilled"]{display:none}`） |
| 數量上限 | 寫在各站檔案 |

共用 class：`.kh-ad`（width:100%、max-width:728px）、`.kh-ad--game`（上方 150px）、`.kh-lift`（z-index 6）、`.kh-legal`。

---

## 5. Travelpayouts 共用規則

- Drive：放 `<head>` 第一個 script，所有頁面含 404。上線後到後台按「驗證」。
- 手動聯盟連結：`rel="sponsored nofollow noopener"`；區塊下方寫揭露（有回饋、價格不會變貴、無審稿關係）；不對價格、優惠、匯率做斷言；連結集中放在設定物件，不散在 HTML。
- WordPress 上的連結網址不能含 `&`。

---

## 6. Cookie 與隱私（.kh-legal）

每頁頁尾一行，依頁面語言：

- 中：本站使用 Cookie 進行流量分析（Google Analytics）與顯示廣告（Google AdSense），部分連結為聯盟連結。隱私權政策
- en：This site uses cookies for analytics (Google Analytics) and ads (Google AdSense), and some links are affiliate links. Privacy
- ja：当サイトはアクセス解析（Google Analytics）と広告配信（Google AdSense）のためにCookieを使用し、一部にアフィリエイトリンクを含みます。プライバシーポリシー

---

## 7. 品牌與 SEO 基本項

- **分頁圖示**：所有子網域用編織日和系列的 favicon（米色底、白色拱窗），檔案以 games 的 `/icons/` 為準。分頁圖示只用在分頁，不當品牌 logo。
- **頁首品牌列**（2026-10-04 起）：所有子網域（story、tools、games、poem、study）的每一頁，**最上方**都放「正式 logo＋『編織日和・站名』文字」，點了回**該子網域的首頁**。作品／工具／遊戲名稱放在品牌列下方，不取代品牌。寫法以 games 的 `_template/` 為準（`.kh-brand-row`、`.kh-brand`）。
  - logo 用正式 logo（方形「編織日和 Knitting Hiyori」棒針底圖），檔案以 games 的 `/icons/logo-knitting-120.webp` 為準（高解析度用 `logo-knitting-240.webp`），顯示 40px；旁邊已寫出「編織日和」時 `alt=""`。
  - 文字用靜態 HTML（§8-1），不能只放在圖片裡。站名例：小遊戲、工具、故事、學習筆記（英：編織日和 · Games；日：編織日和・ミニゲーム）。窄螢幕放不下時，先藏站名，「編織日和」不藏。
  - 追蹤：`data-cta="brand_hub"`，`data-cta-type` 填該站類型（games `game`、tools `tool`、story `story`、study `study`；poem ⚠ 待補值域）。不開自動廣告的頁面，連結要有 vignette 標記（§9）。
  - 既有頁面列在 registry 待修清單，改版時補上。
- 每個頁面都要有：**SEO 標題、meta description、英文 slug**、canonical、OG（1200×630 圖）。
- 多語網址：中文在根目錄，英日加 `/en/`、`/ja/` 前綴，slug 三語相同（例：tools `/<slug>/`、`/en/<slug>/`、`/ja/<slug>/`）。**games、story 例外**：英日放在作品資料夾裡（games `/<slug>/en/`；story `/<類別>/<作品>/en/`），一個作品一個資料夾、整包上傳。互設 hreflang，`x-default` 指中文；`<html lang>` 為 `zh-Hant-TW`／`en`／`ja`。
- FAQ 的 JSON-LD 必須和頁面文字逐字一致。404 加 `noindex`。
- 中文內容使用全形標點；版面以手機閱讀為優先（390px 先做對）。

---

## 8. 工程原則

1. 文字一律靜態 HTML，JS 只負責行為；爬蟲與 AI 不執行 JS 也抓得到全部內容。
2. 每個互動元件各自 try/catch。
3. 動畫只用 transform／opacity，並尊重 `prefers-reduced-motion`。
4. 文字顏色上線前算 WCAG 對比（一般 4.5、大字 3.0），不憑肉眼。
5. 輸入框字級至少 16px；按鈕最小高度 44px。

---

## 9. 共用驗收項目

各站檔案可以加項目，但不能少於這些：

- 390px／1200px 無橫向溢出
- WCAG AA 對比 0 筆不合格
- JSON-LD 可解析、FAQ 逐字一致
- Drive 是 head 第一個 script；AdSense 載入碼與單元數量符合該站規則；所有連結有 vignette 標記（不開自動廣告的站）
- 擋掉 GA4／AdSense／Drive 時功能照常；Console 無錯誤
- `?hy_debug=1` 操作一輪，參數值沒有中文、讀者輸入的文字或 (not set)
- 追蹤碼「和號」字元數為 0
- `spec-version` meta 存在且是目前版本
- 頁首最上方有品牌列：正式 logo＋「編織日和」文字，連到該子網域首頁（§7）
