# tools.knittinghiyori.com 規範

**版本：tools-v2.2.1｜2026-10-04**（由 tools-guideline v2.1 拆出；共用部分已移到 `core.md`，這裡只寫 tools 專屬）
負責人：Alison（改本檔的規則需 Alison 確認）；新增工具時在 `registry.md` 登記；合併進 main 由 Zoe 統一處理（見 core §0）。先讀 `core.md`。

---

## 1. 網站結構

- GitHub Pages，`main`／root，自訂網域 `tools.knittinghiyori.com`（Cloudflare CNAME `tools` → `<帳號>.github.io`）。

```
/                      總覽頁（中文）       ← build.py 產生
/en/  /ja/             總覽頁（英、日）     ← build.py 產生
/404.html  /sitemap.xml  /robots.txt  /CNAME  /llms.txt  ← build.py 產生
/assets/style.css  app.js  favicon.svg      總覽頁共用
/assets/site.css       工具頁共用外框（k- 開頭的 class）
/assets/tools/<工具>.css／.js   各工具樣式與程式
/tools.json            工具清單（總覽頁資料來源）
/build.py              產生器
/tool_pages.py         工具頁產生器
/<slug>/  /en/<slug>/  /ja/<slug>/   工具頁三語版   ← build.py 產生
/_src/<工具>/          工具頁原始檔（robots.txt 已擋）
/wp-src/<slug>/        還沒搬家的 WordPress 工具原始檔與載入器產生腳本（robots.txt 要擋）
```

- **改總覽頁只改 `tools.json` 或 `build.py`**，再跑 `python3 build.py`；直接改 index.html 會被覆蓋。
- 新工具一定要在 `tools.json` 加一筆（圖示加在 `build.py` 的 `ICONS`），sitemap、llms.txt 自動收錄。
- 還沒搬家的 WordPress 工具，總覽頁卡片直接連回 WP 原網址。
- 季節訂房倒數（`season_booking`）：原規劃放 games，改由 Alison 直接在 tools 製作（/season-booking/），games 不上線。

## 2. 本站固定值與 `<head>` 範例

值見 `core.md` §1（tools 那一列）。`<head>` 順序見 `core.md` §2，範例：

```html
<script data-cfasync="false" data-cmp-ab="2">(function(){var s=document.createElement("script");s.async=1;s.setAttribute("data-cmp-ab","2");s.src="https://emrld.ltd/NTc5OTI2.js?t=579926";document.head.appendChild(s)})();</script>
…
<link rel="icon" href="/favicon.ico" sizes="any">
<link rel="icon" type="image/png" sizes="32x32" href="https://games.knittinghiyori.com/icons/favicon-32.png">
<link rel="apple-touch-icon" href="https://games.knittinghiyori.com/icons/apple-touch-icon.png">
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js" crossorigin="anonymous"></script>
<script async src="https://www.googletagmanager.com/gtag/js?id=G-ZQZHTYTRMQ"></script>
<script>window.dataLayer=window.dataLayer||[];function gtag(){dataLayer.push(arguments)}gtag("js",new Date());
gtag("set",{content_group:"tool",tool_id:"<tool_id>",page_lang:"zh-Hant",page_title:"工具|名稱|做什麼"});
gtag("config","G-ZQZHTYTRMQ");</script>
```

- `content_group` 一律 `tool`（總覽頁也是）。

## 3. GA4（tools 專屬）

### 3-1 工具共用事件（在 core §3-2 之外）

| 事件 | 觸發 | 參數 |
|---|---|---|
| `tool_start` | 第一次點擊或輸入工具區 | `entry_point` |
| `tool_result` | 第一次得到結果（範例不算） | 依工具，例：`item_count` |
| `tool_demo`、`tool_reset`、`tool_restore` | 載入範例、清空、還原 | — |
| `open_shared` | 打開別人分享的結果 | 依工具 |

- 工具專屬事件命名 `{前綴}_{動詞}`；能用共用事件就不另開。前綴先到 `core.md` §3-5 登記。

### 3-2 工具登記表

移到 `registry.md`。新工具開工前先在那裡加一列。

### 3-3 總覽頁 `hub` 的事件

| 事件 | 觸發 | 參數 |
|---|---|---|
| `cta_click` | 點工具卡片 | `cta_id`＝`hub_card`／`hub_feature`／`hub_recent`／`hub_omikuji`、`cta_type=tool`、`option`＝目標 tool_id、`card_index`、`link_url` |
| `cta_click` | 其他連結 | `promo_games`／`footer_games`（game）、`footer_blog`（article） |
| `hub_filter` | 點分類（「全部」不送） | `option`＝travel／learn／life／social／money／work、`source=category` |
| `hub_search` | 停止輸入 1.2 秒 | `item_count`、`result`＝hit／miss（不送搜尋字） |
| `hub_omikuji` | 抽籤 | `option`＝tool_id、`source`＝hero／again |
| `lang_switch`、`share`／`share_cancel` | — | 見 core |

### 3-4 工具頁導流 CTA

`related`（tool）、`blog_read`（article）、`blog_home`（article）、`back_hub`（tool）、`games_hub`（game）、`header_hub`、`footer_*`。

## 4. AdSense 數量與位置

- **工具頁最多 2 個，總覽頁 1 個**。
- 工具頁：教學段之後、FAQ 之前；總覽頁：工具列表之後、games 推廣卡之前。
- 工具頁要有足夠說明文字，內容過少會被判不符資格。

```html
<aside class="kh-ad-wrap" aria-label="廣告"><div class="kh-ad">
<p class="kh-ad-l">廣告</p>
<ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-2022028565680247" data-ad-slot="3114811513" data-ad-format="auto" data-full-width-responsive="true"></ins>
<script>(adsbygoogle=window.adsbygoogle||[]).push({});</script>
</div></aside>
```

## 5. 版型

- 白底黑字、一個強調色（套印紅）、印刷／編輯物語彙（細線、等寬字小標、No.01／§ 01 編號）。
- 每個工具可有自己的主題概念，但色票、字體、元件尺寸用下面的共用值。

| 角色 | 色碼 | 對白底 |
|---|---|---|
| 紙 | `#ffffff` | — |
| 主文字 | `#16120f` | 18.6 |
| 次文字 | `#5a524e` | 7.6 |
| 標籤文字 | `#6f6764` | 5.5（不可再淡） |
| 強調 | `#c8341e` | 5.3 |
| 強調淡底 | `#fbebe7` | 紅字在上 4.6 |
| 確認綠 | `#1d6b45`／底 `#e8f3ec` | 6.5（淡底上 5.7） |
| 底塊 | `#f7f4f2` | — |
| 分隔線 | `#e4deda`（深 `#cfc6c1`） | — |

| 角色 | 字體 | 載入 |
|---|---|---|
| 英文標題、數字 | Instrument Serif | Google Fonts |
| 中日標題 | Noto Serif TC／JP（600、900） | **只能用 `&text=` 子集** |
| 標籤 | IBM Plex Mono | Google Fonts |
| 內文 | 系統 CJK 堆疊 | 不載入 |

- 卡片圓角 14–24px、1px 細框；手機留白 20px、桌機 40px；內容最大寬 1240px；主要按鈕 52px。

## 6. 工具頁固定結構（`tool_pages.py`）

頁首（品牌＋語言切換）→ 麵包屑 → 工具（H1、一句話說明、操作區、聯盟推薦）→ 教學（HowTo）→ 廣告 → FAQ → 同分類相關工具 4 個 → 部落格延伸閱讀 3 篇 → 看全部工具／遊戲兩張大卡 → 收藏＆分享 → 頁尾。

- JSON-LD：工具頁 WebApplication＋HowTo＋FAQPage＋BreadcrumbList；總覽頁 CollectionPage＋ItemList＋FAQPage。
- 英日介面文字 build 時換好（`data-t`），爬蟲不執行 JS 也看得到；英日教學與 FAQ 另外寫，不直翻。
- 原始檔：`_src/<工具>/` 下 `meta.json`、`top.html`、`art.zh|en|ja.html`（`<!--AD-->` 標廣告位置）、`install.html`、`tail.html`、`i18n.json`、`style.css`、`main.js`。
- 只有中文的新工具：直接放 `/<slug>/index.html`，`tools.json` 設 `"page": "<slug>"`，不設 hreflang。

## 7. 搬家規範（WordPress → tools）

1. 取得線上原始碼 → 拆成 `_src/<工具>/`，語言改由網址決定。
2. 寫英日教學與 FAQ、填 `meta.json`；`tools.json` 改新網址並加 `"src"`。
3. `python3 build.py` → 跑驗收。
4. 上傳 GitHub，確認三個網址可開。
5. WordPress 設 301（Rank Math → 重新導向：來源 `tools/<slug>` 完全符合 → `https://tools.knittinghiyori.com/<slug>/`），原頁 noindex。
6. GSC 要求建立索引。
7. 部落格內舊連結慢慢改新網址。
8. 本檔 §3-2 狀態改「已搬家」。

- slug 沿用 WordPress 的英文 slug。
- 順序：**不搬（2028 前）** 顏文字、小樹點換哩程；**第一批** 旅費分帳（完成）→ 聚餐分帳 → JR Pass → 行李清單 → eSIM → 日文闖關 → YouTube 逐字稿 → QR Code → 名片 QR → UTM → 貼文排版；**第二批（搬前記錄排名）** 日股代號、定期定額、IG 特殊符號、旅遊優惠；文章型工具（織女安檢、拍立得）先不搬。
- 每搬一個等 2 週看 GSC，再搬下一個。
- 已知影響：localStorage 依網域分開，舊網址存的資料在新網址看不到；分享連結（# 帶資料）不受影響。

## 8. 驗收（在 core §9 之外）

- 三語 × 390／1200 × 初始／操作後，各跑一次。
- 累積的 bug 通則：
  1. `li` 內有行內元素時不用 grid 排編號。
  2. 有 `hidden` 屬性的元素不寫 inline `display:flex`；加 `[hidden]{display:none}`。
  3. SVG `<textPath>` 環形文字用 `textLength` 固定長度。

## 9. 部署（新工具）

1. 放 `/<slug>/index.html`（或 `_src/`）→ 本機 `python3 -m http.server 8000` 跑驗收。
2. `tools.json` 加一筆、`ICONS` 加圖示 → `python3 build.py`。
3. 推到 `alison/<主題>` 分支並開 PR（工具頁、重新產生的三語 index、sitemap 都要包含），由 Zoe 合併。
4. GSC 要求索引；§3-2 登記；有新參數才註冊自訂維度；Travelpayouts 後台確認 Drive。
