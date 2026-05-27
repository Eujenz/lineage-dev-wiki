# 天堂私服 | AI Agent 對話檔設計引導

## 章節用意

本篇提供給 AI Agent 使用，目標是讓 Agent 在新增、修改或批量生成 2.70C 對話檔時，同時符合：

- 2.70C client 可解析的 HTML-like 語法。
- Big5 中文編碼限制。
- 既有對話檔的口吻與世界觀。
- `link`、`action`、`var` 與伺服器互動分工。
- 可維護、可測試、可被後續系統重用。

若 Agent 只需要工程規則，先讀 093 到 104；若 Agent 需要寫出符合世界觀的內容，先讀 105，再讀本篇。

## Harness Engineering 原則

本篇的核心不是讓 AI「自由創作」，而是把 AI 放進可驗證的工作框架。Harness Engineering 在這裡指的是：替 Agent 建立輸入契約、資料夾具、生成邊界、驗證閘門與可追蹤輸出，讓每一次產出的對話檔都能被重跑、比對、修正與測試。

Agent 應遵守以下原則：

- 明確輸入：任務開始前先確認 `html_id`、NPC 身份、用途、世界觀主題、互動行為與伺服器需求。
- 固定夾具：生成前必須引用同類原生對話檔，不可只依模型記憶或標準 HTML 經驗。
- 小步輸出：先產出互動規格，再產出 HTML，再產出測試清單。
- 約束優先：語法白名單、Big5、`link/action/var` 分工比文案華麗更重要。
- 可觀測性：每個 `action`、`link`、`var` 都要能追溯用途與測試方式。
- 失敗可恢復：遇到不確定標籤、編碼、action 或世界觀衝突時，先降級到保守模板。

## Agent Harness 結構

每次新增或修改對話檔，建議把任務拆成五層 harness：

```text
Input Contract  ->  Retrieval Fixture  ->  Generation Gate  ->  Validation Gate  ->  Delivery Report
輸入契約        ->  語料夾具           ->  生成閘門         ->  驗證閘門       ->  交付報告
```

### 1. Input Contract：輸入契約

Agent 在寫任何 HTML 前，必須先得到或自行整理以下欄位：

```text
request_id:
html_id:
npc_name:
npc_role:
page_type:
world_theme:
player_goal:
server_actions:
dynamic_data:
source_dialogs:
acceptance_criteria:
```

欄位說明：

- `page_type`：純文字、導覽、任務、製作、傳送、倉庫、商店、狀態顯示、活動。
- `world_theme`：亞丁守護團、拉斯塔巴德、殷海薩、格蘭肯、四龍、妖精森林、古代遺產等。
- `server_actions`：需要伺服器處理的 action 名稱與目的。
- `dynamic_data`：`<var src="#n">` 對應的 data 陣列。
- `source_dialogs`：至少 1 到 3 個同類原生對話檔作為語氣與格式依據。
- `acceptance_criteria`：此頁被視為完成的測試條件。

如果資訊不足，Agent 只能產出「待確認規格」，不要直接產出最終對話檔。

### 2. Retrieval Fixture：語料夾具

Agent 必須先找原生範本，再生成新內容。推薦檢索規則：

```text
同系統優先 > 同 NPC 類型 > 同世界觀主題 > 同頁面互動模式
```

例如新增拉斯塔巴德鐵匠製作頁時，夾具優先順序：

```text
adelio*.html      拉斯塔巴德與真冥皇製作
koupa*.html       高階裝備修改
alchemy*.html     材料轉換與屬性石
detecter*.html    古代裝備封印解除
```

夾具不是拿來複製文字，而是拿來約束：

- 標題長相。
- 行距與 `<br>` 使用。
- 選項數量。
- 材料清單格式。
- NPC 對玩家的稱呼。
- action/link 的使用時機。

### 3. Generation Gate：生成閘門

Agent 只有在互動規格通過後，才開始產出 HTML。生成時遵守：

- 一個頁面只處理一個主要目的。
- 每頁選項維持 1 到 5 個，避免塞成選單牆。
- 文字優先短句，單行避免過長。
- 需要狀態判斷的選項一律使用 `action`。
- 純說明或固定章節才使用 `link`。
- 動態數值與狀態只用 `<var src="#n">`，不要硬寫。
- 不確定 client 是否支援的標籤，不使用。

### 4. Validation Gate：驗證閘門

產出後必須用檢查清單驗證。至少包含：

```text
syntax_check:
encoding_check:
link_action_check:
var_mapping_check:
lore_check:
voice_check:
server_contract_check:
client_click_test:
```

驗證標準：

- `syntax_check`：只使用白名單標籤。
- `encoding_check`：中文可保存為 Big5。
- `link_action_check`：靜態跳頁與伺服器 action 沒有混用。
- `var_mapping_check`：`#0`、`#1`、`#2` 與 data[] 順序一致。
- `lore_check`：世界觀詞彙沒有跨主題亂混。
- `voice_check`：NPC 口吻符合身份。
- `server_contract_check`：每個 action 都有伺服器端處理計畫。
- `client_click_test`：最終仍需 client 實際點擊確認。

### 5. Delivery Report：交付報告

Agent 最終輸出不可只貼 HTML，必須附上可追蹤報告：

```text
changed_files:
html_ids:
source_dialogs:
actions:
data_mapping:
validation_result:
manual_test_needed:
known_risks:
```

## Agent 工作流程

### 1. 先判斷對話檔用途

新增或修改前，先把頁面歸類：

```text
純文字說明頁
靜態分頁導覽
任務接取/回報頁
道具製作/兌換頁
傳送/倉庫/商店等服務頁
狀態顯示頁
圖片按鈕頁
活動頁
```

判斷規則：

- 不需要伺服器判斷狀態：使用 `link`。
- 需要扣道具、給獎勵、檢查任務、傳送、買賣、倉庫、製作：使用 `action`。
- 需要顯示價格、狀態、數量、完成標記：使用 `<var src="#n">`。

### 2. 先找同類原生範本

Agent 不應直接從標準 HTML 經驗推測 client 支援度。應優先找同類原生檔：

```text
鐵匠/製作     adelio*.html, koupa*.html
傳送服務       *teleport*, elleris*.html
倉庫服務       denitz-c.html 類型
古代裝備       detecter*.html
龍與英雄試煉   cray*.html
妖精/米索莉    doette*.html, nerupa*.html
說明卷軸       tscroll*.html
```

同類範本要觀察：

- 標題格式。
- 每行長度。
- 選項數量。
- 使用 `link` 還是 `action`。
- 是否使用 `<var src="#n">`。
- 文字是命令式、請求式、說明式或祝禱式。

### 3. 產出前先寫互動規格

在寫 HTML 前，先產出簡短規格：

```text
html_id:
用途:
NPC:
玩家入口:
需要伺服器 action:
需要 data[]:
會跳轉的 link:
世界觀關鍵詞:
```

範例：

```text
html_id: icforge1
用途: 拉斯塔巴德材料鍛造入口
NPC: 侏儒鐵匠
玩家入口: 點擊 NPC talk
需要伺服器 action: icforgeMake1
需要 data[]: #0=黑暗的錠數量, #1=魂晶數量
會跳轉的 link: icforgeHelp
世界觀關鍵詞: 拉斯塔巴德, 格蘭肯的淚水, 黑暗礦石
```

## 對話檔語法規範

### 基本模板

```html
<body>
<font fg=ffffff><p align=left>NPC名稱：</p></font>
<br>
對話文字。<br>
<br>
<a link="pageid">靜態說明</a><br>
<a action="serverAction">執行行動</a><br>
</body>
```

### 編碼

- 中文檔案使用 Big5。
- 檔名沿用 `xxx-c.html`。
- 若工具鏈以 UTF-8 編輯，最後輸出前必須轉 Big5。
- 避免使用 Big5 不穩定字元；若 client 顯示異常，改用常見替代字。

### 標籤白名單

優先使用：

```html
<body>
<font fg=ffffff>
<p align=left>
<br>
<a link="...">
<a action="...">
<img src="#331" link="..."></img>
<img src="#331" action="..."></img>
<var src="#0">
<username>
```

謹慎使用：

```html
<b>
<name>
```

避免使用：

```html
<div>
<span>
<table>
<button>
<input>
CSS
JavaScript
標準 HTML color 屬性
```

### link/action 命名

原生檔可見含空格或短字母 action，但自訂系統建議穩定命名：

```text
collectionList1
collectionDetail34
forgeMakeDarkIngot
questReportAden1
teleportAdenCave
```

命名原則：

- 使用英數。
- 避免空格與標點。
- prefix 表示系統，suffix 表示頁碼或狀態。
- action 名稱必須能在伺服器端清楚對應。

## 世界觀寫作規則

### 不要寫成現代網頁文案

不建議：

```text
歡迎使用本功能，請點擊下方按鈕查看獎勵列表。
```

建議：

```text
你帶來的證物我已經確認過了。這是亞丁守護團答應給勇士的補償。
```

### 任務動機要來自世界

常用動機：

```text
戰後殘兵仍未投降
村民受到妖魔或變形怪威脅
聖堂需要捐款維持傳送
工匠需要秘技書與材料
古代裝備仍被封印
黑暗妖精需要證明忠誠
四龍災厄留下傷痕
```

### 材料清單要保留原生口吻

原生製作對話常直接列出材料，適合保留這種務實感：

```html
<body>
<font fg=ffffff><p align=left>侏儒鐵匠：</p></font>
<br>
想要修復這件裝備，就把以下材料帶來。<br>
黑暗的錠 <var src="#0"> 個<br>
格蘭肯的淚水 <var src="#1"> 個<br>
暗黑妖精之魂的結晶 <var src="#2"> 個<br>
<br>
<a action="forgeDarkArmor">材料已經準備好了</a><br>
</body>
```

### NPC 口吻模板

王國軍官：

```text
你已經取得證物了嗎？亞丁不會忘記為王國流血的勇士。
```

村民：

```text
戰爭說是結束了，可是村外還是很危險。拜託你，幫幫我們吧。
```

侏儒鐵匠：

```text
東西不是不能做，但材料少一樣都不行。尤其是那本秘技書，沒有它我也無能為力。
```

神官：

```text
願殷海薩的祝福與你同在。若你要前往危險之地，請先做好準備。
```

黑暗妖精守衛：

```text
光是外表像我們，並不能證明你不是拉斯塔巴德派來的眼線。
```

古代靈魂：

```text
長久以來，我等待的不是強者，而是能承受這份意志的人。
```

傳送師：

```text
你要前往哪裡？路途越危險，所需的費用也越高。
```

倉庫管理員：

```text
把東西放在我這裡，比丟在地上安全多了。領取時別忘了費用。
```

## AI 生成檢查清單

### Preflight：產出 HTML 前

- 是否先確認用途分類。
- 是否有同類原生範本。
- 是否列出 `source_dialogs`，且每個來源都有用途。
- 是否決定 `link`/`action`/`var` 分工。
- 是否列出伺服器端需要處理的 action。
- 是否列出 data 陣列順序。
- 是否使用 105 的世界觀詞彙，而不是憑空創造現代詞。
- 是否定義完成條件，例如「點擊製作後扣除材料並回傳成功/失敗頁」。

### Static Validation：產出 HTML 後

- 是否只使用 client 穩定支援標籤。
- 是否避免 CSS/JS/table/input。
- 是否每個選項後有 `<br>`。
- 是否避免過長單行。
- 是否 action 名稱可被伺服器辨識。
- 是否 `<var src="#n">` 與 data[] 對應。
- 是否 Big5 可保存。
- 是否每個頁面都有可回到入口或上一層的路徑。

### Runtime Validation：進遊戲後

- 是否能由 NPC 正確打開 `html_id`。
- 是否所有 `link` 都能跳到預期頁面。
- 是否所有 `action` 都能被伺服器 log 或 handler 捕捉。
- 是否不足材料、任務未完成、金幣不足等失敗情境都有回應頁。
- 是否 `<var src="#n">` 顯示正確數值，沒有空白、錯位或殘留替代符。
- 是否 Big5 中文沒有亂碼。
- 是否圖片按鈕可點擊，且不遮蔽文字。

## Definition of Done

一組對話檔只有同時符合下列條件，才算完成：

```text
DoD-1: 有 input contract。
DoD-2: 有至少一個同類原生 source_dialog。
DoD-3: 每個 link/action/var 都有用途說明。
DoD-4: HTML 只使用白名單或已驗證標籤。
DoD-5: 中文可轉存 Big5。
DoD-6: 伺服器 action 合約已列出。
DoD-7: 成功與失敗流程都能回到可理解頁面。
DoD-8: 世界觀與 NPC 口吻通過檢查。
DoD-9: 已列出 client 實測項目。
```

若無法完成 `DoD-6` 或 `DoD-9`，交付報告中必須標示為 `manual_test_needed: true`。

## Agent 輸出格式建議

當 Agent 被要求新增對話檔時，建議輸出以下內容：

```text
1. Input Contract
2. Retrieval Fixture
3. Interaction Spec
4. Server Contract
5. HTML Files
6. Data Mapping
7. Validation Result
8. Manual Test Checklist
9. Known Risks
```

範例：

```text
Input Contract:
- request_id: aden_badge_reward
- html_id: adenbadge1-c.html
- npc_name: 亞丁守護團員
- npc_role: 王國軍官
- page_type: 任務回報
- world_theme: 亞丁守護團, 拉斯塔巴德殘兵
- player_goal: 交出黑暗妖精徽章並取得補償

Retrieval Fixture:
- eno1-c.html: 亞丁守護團徽章回收口吻
- montes15-c.html: 戰後殘兵討伐背景

Server Contract:
- adenBadgeReward: 檢查黑暗妖精士兵徽章數量並給予補償
- adenBadgeHelp: 回傳任務說明頁或固定 link

Data Mapping:
- #0: 目前持有徽章數量
- #1: 可領取補償金額

Validation Result:
- syntax_check: pass
- encoding_check: pending
- client_click_test: pending
```

## 常見錯誤

### 錯誤 1：把整頁動態 HTML 塞進 data

不建議把整頁 HTML 當 data 傳給 client。穩定做法是固定 `html_id`，再用 `<var src="#n">` 填入短文字或數值。

### 錯誤 2：把 link 用在需要狀態判斷的流程

例如製作、兌換、任務回報、傳送都應使用 `action`，因為伺服器必須檢查角色狀態。

### 錯誤 3：過度現代化 NPC 口吻

原生對話多半簡短、直接，且常從 NPC 的身份立場說話。不要加入「系統提示」「功能介紹」「點擊按鈕」等現代 UI 文案。

### 錯誤 4：世界觀混用

不要把殷海薩祝福、格蘭肯詛咒、伊娃水系、拉斯塔巴德黑暗軍團、四龍災厄混成同一個無差別詞庫。除非任務就是跨陣營衝突，否則每個系統應有主題邊界。

### 錯誤 5：沒有失敗頁

只寫「材料已經準備好了」的成功 action，卻沒有材料不足、金幣不足、任務未達成、背包不足等失敗回應，會讓玩家誤以為 client 或 server 壞掉。每個會改變狀態的 action 都至少要規劃成功與失敗頁。

### 錯誤 6：沒有保留來源依據

Agent 產出看起來像天堂文字，但沒有列出參考哪幾個原生檔，後續就很難判斷這是語料推導還是模型臆造。所有新增世界觀、口吻、材料命名都應回到 `source_dialogs` 或標示為衍生設定。

## 可交給 Agent 的任務範本

### 任務範本：新增製作 NPC

```text
請依照 2.70C 對話檔規則，新增一組侏儒鐵匠製作頁。
世界觀主題使用拉斯塔巴德與格蘭肯材料。
需要首頁、材料說明頁、製作 action 頁。
請依照 Harness Engineering 輸出 Input Contract、Retrieval Fixture、Server Contract、HTML、Data Mapping、Validation Result。
每個 action 都要有成功頁與失敗頁規劃，並列出 Big5 注意事項。
```

### 任務範本：新增收藏圖鑑

```text
請設計一組收藏圖鑑對話檔。
主題為四龍遠征。
列表頁要顯示完成狀態，使用 <var src="#n">。
詳細頁使用 action 回伺服器取得角色進度。
文字口吻要像古代靈魂或遠征記錄，不要像現代 UI。
請列出 source_dialogs，並說明每個頁面的 link/action/var 分工。
```

### 任務範本：修正既有對話檔

```text
請檢查這批對話檔是否有不穩定標籤、錯誤 link/action 分工、過長單行、Big5 風險字、缺少返回頁。
請依照 Validation Gate 輸出 syntax_check、encoding_check、link_action_check、var_mapping_check、lore_check、voice_check、server_contract_check。
請輸出修正建議、修改後 HTML，以及仍需 client 實測的項目。
```

## 推進建議

1. 建立一個 `dialog_agent_skill.md`，把本篇濃縮成 Agent system prompt。
2. 建立 `dialog_templates/`，收納鐵匠、神官、守衛、傳送師、倉庫、古代靈魂等模板。
3. 建立 lint 工具檢查標籤白名單、action 命名、Big5 編碼、`var` 序號連續性。
4. 建立語料索引，把每個世界觀詞彙連回代表對話檔，方便 Agent 引用來源。
