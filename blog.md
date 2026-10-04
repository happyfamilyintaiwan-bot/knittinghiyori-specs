# knittinghiyori.com（WordPress 部落格）規範

**版本：blog-v1.0.1｜2026-10-04**
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

## 4. ⚠ 待補

- AdSense 在部落格的設定（自動廣告？slot？）、Travelpayouts 在部落格的用法、文章 SEO 標題格式。
