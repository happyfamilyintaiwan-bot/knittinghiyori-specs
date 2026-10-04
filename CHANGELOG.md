# CHANGELOG

新的寫在最上面。格式：`日期｜檔案 版本｜誰｜改了什麼｜為什麼`

---

- 2026-10-04｜study v0.2｜Zoe｜設計從「日系清新筆記風」改成「日系筆記本骨架＋中性專業調性」；首頁加「目次」，新增 cta_id `toc_link`；各頁 spec-version 改 `core-v1.3/study-v0.2`｜可愛風偏女性向，study 要照顧男女讀者並增加專業感

- 2026-10-04｜games v1.4.1｜Zoe｜404 頁依語言切換（網址 /ja/、/en/ 或瀏覽器語言），有該語言版的遊戲排前面；§7 主頁交接加「404 多語卡片」｜從英日遊戲頁迷路的讀者看得懂，並直接回到該語言的遊戲

- 2026-10-04｜core v1.3、registry v1.2、study v0.1（新增）｜Alison 提案、Zoe 定案｜新增 study 子網域（學習筆記），id 參數 `topic`（連字號）、content_group=`study`、cta_type 加 `study`、§7 品牌列加 study；core §0 分工改成「Alison 只交內容（4 項），所有上架由 Zoe 的 Claude Code 處理」，表格欄名改「內容負責人」，存檔流程改 `zoe/<主題>` 分支；Alison 原提的「兩人皆可編寫」因新分工不需要，未採用｜Alison 要整理課程與自學筆記，分開子網域報表才分得清楚；Alison 改用 claude.ai 寫內容，不再操作 repo
  - study 首頁主題卡暫時直接連各主題的部落格主力文章，筆記上線後改回主題頁；404 的 cta_id 對齊 games（`notfound_hub`、`notfound_topic`）

- 2026-10-04｜games v1.4｜Zoe｜§1 新增分頁圖示（正式 logo 整組＋根目錄 favicon.ico、apple-touch-icon.png、`?v=N`）與 404 頁規格；§3-5 加 `notfound_hub`、`notfound_game`；遊戲主頁補品牌列；所有 games 頁 spec-version 的 games 段改 v1.4｜Zoe 指定分頁圖示用統一品牌 logo；根目錄缺 favicon 會顯示灰色地球；404 要引導讀者回主頁看更多遊戲
  - ⚠ core §7「分頁圖示：米色底、白色拱窗」與 games 現況不同，待兩人確認後改 core（共管）

- 2026-10-04｜games v1.3.1｜Zoe｜§1 新增 og 圖規則：左上角品牌列（正式 logo＋編織日和・小遊戲）、網址寫到遊戲路徑、換圖用新檔名｜分享預覽被縮小或轉傳時仍看得出是編織日和；絕對音感三語換成 og-2.png，其他遊戲在下一批檢查時套用

- 2026-10-04｜games v1.3｜Zoe｜新增 §6-1 成績卡圖片（1080×1350、浮水印＋金色品牌列、分享／下載／複製連結與追蹤值）；絕對音感試點上線，三頁 spec-version 改 `core-v1.2/games-v1.3`、頁尾改 core v1.2 新文字｜讓玩家把成績帶著遊戲網址分享出去，圖被轉傳也找得回來
  - 其他 6 款仍是 `core-v1.1/games-v1.2.1`，頁尾與聯盟 cta_type 在下一批（registry 待修）一起改

- 2026-10-04｜core v1.2、registry v1.1.1｜Alison 提案、Zoe 定案｜core §7 新增「頁首品牌列」、§9 驗收加一項；registry 莫斯科紳士補上線紀錄、待修清單加「既有頁面補品牌列」｜讀者從任何作品／工具／遊戲頁進來都知道是編織日和做的；和 Zoe 的 v1.2 同日都未合併，併成同一批發布避免撞號
  - 寫法對齊已上線的 games 品牌列：cta_id 統一 `brand_hub`、點了回該子網域首頁、cta_type 填該站類型（Alison 草案原為 `header_brand`／`other`、連主站，Zoe 定案改成和 games 一致，GA4 一次篩得出全部子網域）
  - logo 用正式 logo `logo-knitting-120.webp`（40px），不用分頁圖示
- 2026-10-04｜core v1.2、story v1.2｜Zoe｜hy-story.js 預設送 content_group=story、work（story_id 過渡期一起送），interaction_id 不送畫面文字、page_lang 只送值域內的值；首頁卡片 cta_type story_card → story，core §3-3 值域加 story；core §6 頁尾改「部分連結為聯盟連結」（英日同步）；追劇 4 部 8 頁的舊內嵌追蹤改送 story／work｜Alison 建議，追劇與小說報表一致；小說頁的聯盟是蝦皮
  - **改版日 2026-10-04**：追劇的 content_group 之前是 `interactive-story`，看長期趨勢要合併
  - 頁尾文字：新頁照新寫法；舊頁改版時順便更新
- 2026-10-04｜registry v1.1.1、story v1.2｜Alison｜莫斯科紳士上線 /books/a-gentleman-in-moscow/，registry 改已上線；story §3-1 定案：作品頁都載入 hy-story.js，需帶參數的 CTA 用頁面自己的屬性避免重複，interaction 元素加 data-interact；§5 補互動元件慣例；§6、§8 更新｜統一互動頁追蹤條件，books 與 drama 共用同一支追蹤

- 2026-10-04｜games v1.2、v1.2.1｜Zoe｜§2 頁面結構加「0. 編織日和品牌列」、§3-5 CTA 表加 `brand_hub`｜品牌列已套到全部 7 款遊戲與 `_template/`，各頁 spec-version 改 `core-v1.1/games-v1.2`；遊戲頁被截圖或嵌入時仍看得到品牌，點了回主頁
  - **改版日 2026-10-04**：之前沒有 `brand_hub`，看「從遊戲回主頁」的總量要合併 `about_hub`＋`brand_hub`
  - v1.2.1：品牌列 logo 由拱窗圖示換成正式 logo `/icons/logo-knitting-120.webp`（40px）；多語頁 400px 以下藏「・小遊戲」｜Zoe 指定正式 logo；只改外觀，不影響追蹤

- 2026-10-04｜core v1.1、registry v1.1、story v1.1、games v1.1、tools v2.2.1、poem v0.1.1、blog v1.0.1｜Zoe＋Alison｜重新分工＋絕對音感三語，兩份更新包合併成同一批發布｜兩份交接都要升 core v1.1，同日都未 push，合併避免撞號
  - 分工：games、poem、追劇、漫畫歸 Zoe，tools、小說歸 Alison，blog 兩人共管；只有 Zoe 合併進 main，Alison 用網頁版 Claude Code 開分支和 PR；core §0 新增分工表、不越界、放錯位置要轉移、存檔流程（含 DELIVERY 五項、合併方式、確認身份）；各 repo 的 CLAUDE.md 精簡成約 20 行，規則只寫在 core §0；5 部原創故事改列追劇（registry 狀態改「待修」，自動廣告改成不開）；story 新增漫畫類型與 page_title 格式，hub 分三區；season_booking、concert_trip 修正為規劃中（實際尚未上線）；tools 新增 wp-src/｜分工明確、main 只有一個出口，桌機與 GitHub 都保有完整檔案
  - 依實際 repo 更正交接文件：story 首頁與 5 部原創追劇都在 `story` repo（沒有 `happyfamilyintaiwan-bot.github.io` repo，原創追劇也不是獨立 repo）；core §1 GitHub 帳號一列改成實際做法：兩人共用同一個帳號，靠 `alison/` 分支與「Alison:」區分，tools 的 main 設保護
  - story 分類別資料夾：`books/`（Alison）、`drama/`（Zoe）、`comics/`（Zoe），既有 7 部追劇搬進 drama/、舊網址留轉址頁；core §7 多語例外加入 story；registry 補登記 amidst-a-snowstorm-of-love、lighter-and-princess；a-gentleman-in-moscow 改規劃中（尚未上線）；games.md、tools.md 移除 season_booking 在 games 的舊說法｜資料夾即負責範圍，作品變多後好溝通、好歸檔
  - 絕對音感（Alison 交件）：core §7 games 多語網址例外改為 /<slug>/en/、/<slug>/ja/；games 加入多語列、HY_GAME_LANG 與 lang_switch 寫法；registry absolute_pitch 補三語名稱、網址與專屬事件｜絕對音感養成所推出英日版；遊戲一個資料夾整包上傳較好管理

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
