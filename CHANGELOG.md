# CHANGELOG

新的寫在最上面。格式：`日期｜檔案 版本｜誰｜改了什麼｜為什麼`

---

- 2026-10-03｜**全部定版**：core v1.0、registry v1.0、tools v2.2、games v1.0（新增）、story v1.0、blog v1.0、poem v0.1（新增）｜Zoe＋Alison｜併入 `05-Alison回覆2.md`｜建立 GitHub 單一來源
  - core §3-2：`cta_id` 記位置（各站自訂）、`cta_type` 記平台；看全部聯盟點擊改用 cta_type 篩
  - core §3-1 #2：註明 story 的 `work` 用連字號是例外；放在 games 的工具仍送 `tool_id`
  - core §3-4：加入遊戲參數 `game_id`、`level`、`correct_count`、`milestone`（⚠ 註冊狀態待核）
  - story：小說／追劇頁關自動廣告加第二步「AdSense 後台網頁排除」
  - registry：狀態加 `擱置`；遊戲前綴確認 `swiftui_`、`jlpt_`（保留）、`flower_`＝flower_shop、`tozai_`（⚠）；新增 concert_trip 完整資料、season_booking（工具表，待修）、shun_tabi（擱置）；新增待修清單
  - **遊戲聯盟 `cta_type` 由 `affiliate` 改為平台名**：改版生效日另記一筆。生效日之前的報表資料是 `affiliate`，看長期趨勢要合併

- 2026-10-03｜story v1.0-draft（新增）、core v1.0-draft3、registry v1.0-draft2｜Zoe｜併入《story 子網域 小說與追劇 追蹤與版型規範 v1》｜Alison 將開始寫小說分析
  - story：GA4 改用全站 G-ZQZHTYTRMQ；購書點擊改 `cta_click`（buy_book／shopee／option=zh,en）；faq、progress、來源連結改用既有參數；自訂維度只需註冊 `work`；小說／追劇頁不開自動廣告
  - core：故事的內容 id 定為 `work`、content_group=`story`；cta_type 加 `shopee`；story 自動廣告改為「首頁與原創故事開、小說／追劇頁不開」
  - registry：新增故事／小說／追劇區

- 2026-10-03｜core v1.0-draft2、tools v2.2-draft2、registry v1.0-draft｜Zoe｜併入 `01-Alison回覆.md`｜統一登記與聯盟點擊寫法
  - 新增 `registry.md`：工具、遊戲的 id 與前綴集中登記；core §3-5、tools §3-2 改為指向它
  - core §3-2：聯盟連結 `cta_type` 一律填平台名，平台不明才用 `affiliate`（回覆衝突 #9）
  - 00 對照表：tools.md 改為「兩邊都可新增工具，改規範需 Zoe 確認」（回覆衝突 #10）
  - 衝突 #11：`telegram` 已在 core §3-3 值域內，不需改動
  - registry 標出待修：`trip_planner`、`jr_pass` 仍為舊寫法；`swift_`／`swiftui_`、`jlpt_` 有無前綴、`flower_`／`tozai_` 待確認

- 2026-10-03｜core v1.0-draft、tools v2.2-draft、blog v1.0-draft｜Zoe｜由 tools-guideline v2.1、subdomain-monetization-notes、wordpress-inline-js-notes 拆出共用規範與站別規範｜建立單一來源，兩個帳號共用
  - core：share `method` 值域加入 facebook／threads／x（依遊戲 v1.0 要求）；`content_type` 加入 game
  - core：前綴登記表補上 v2.1 漏列的 `park_`
  - tools：標出 JR Pass 仍使用舊的 `affiliate_click`，搬家時修正
  - 待 Alison：合併 games v1.0、核對《工具 GA4 v1.2》《故事 GA4 v1.5》原文
