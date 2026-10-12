# DESIGN-STYLE — 法式編輯風（French elegant editorial）

> 版本 v0.8。本文件是介面視覺的單一依據；實作在 `index.html` 樣式表末段的「v0.8 RESTYLE」層與 `:root` 設計變數。

## 1. 原始設計說明（使用者提供，逐字收錄）

來源：使用者提供的設計風格說明（French Elegant Editorial Dashboard Prompt），以及一張參考圖（法式編輯風儀表板：深炭灰側欄、金色鳶尾標誌、奶油色主區、細線圖示、點描印象派風景）。以下原文照錄：

```markdown
# French Elegant Editorial Dashboard Prompt

Create a French elegant editorial dashboard website.

## Style
- Dark charcoal left sidebar with gold accents and refined serif logo
- Soft warm cream / ivory main content area
- Elegant light serif typography (Playfair Display / Didot inspired) for titles
- Delicate thin-line icons
- Generous white space, refined and aristocratic
- Subtle Seurat pointillism texture mixed with Monet Impressionist soft light and atmosphere on background images and decorative elements

## Layout
- Left dark sidebar navigation
- Top greeting with user name
- Row of metric cards
- Large featured landscape or painting area in pointillist Impressionist style
- Lower section with events, collections, and activity cards
- Overall calm, luminous, Parisian sophistication

## Color Palette
- Sidebar: deep charcoal / near black
- Main background: warm cream / soft ivory
- Text: charcoal and soft navy
- Accents: subtle antique gold

## Technical
- Desktop browser mockup
- Clean modern UI with painterly artistic texture
- High-end French editorial / luxury brand aesthetic

## Simplified Version (for quick generation)
French elegant editorial dashboard, dark charcoal left sidebar, warm cream main area, refined light serif titles, delicate thin icons, Seurat pointillism mixed with Monet soft atmospheric light, aristocratic Parisian style, desktop mockup
```

## 2. 設計變數（由參考圖取樣）

### 2.1 顏色

| 角色 | 變數 | 值 | 取樣／用途 |
|---|---|---|---|
| 側欄 | `--sidebar` | `#1F2730` | 參考圖側欄（取樣 #1F2831），深炭灰帶一點墨藍 |
| 側欄第二層 | `--sidebar-2` / `-3` | `#28323E` / `#323D4A` | 側欄輸入框、hover |
| 主背景 | `--cream` | `#F5EFE2` | 暖奶油色主區 |
| 卡片 | `--ivory` | `#FBF7EE` | 卡片、選單、彈出層（取樣 #F6EFDF，略提亮） |
| 紙面 | `--paper` | `#FDFAF3` | 大綱文章、圖解面板、輸入框 |
| 細線 | `--hair` / `--hair-2` | `#E3D8C2` / `#D5C7A9` | 1px 米色細線（卡片框、分隔線）／較強的細線（chip、按鈕） |
| 側欄細線 | `--hair-side` | `rgba(184,149,74,.28)` | 側欄上的金色細線 |
| 主文字 | `--ink` | `#23272D` | 炭灰 |
| 次要文字／標題 | `--navy` / `--navy-soft` | `#2E3D55` / `#56657F` | 柔和墨藍（粗體、副標、箭頭） |
| 弱化文字 | `--muted` / `--muted-2` | `#857D6E` / `#A79E8C` | 說明、提示、計數 |
| 側欄文字 | `--side-ink` / `--side-muted` | `#ECE5D6` / `#9BA2A9` | |
| 古金 | `--gold` / `--gold-deep` | `#B8954A` / `#94763A` | 強調、細線圖示、選取（參考圖鳶尾取樣 #D8B584 → 印刷感調暗） |
| 金色淡底 | `--gold-soft` / `--gold-wash` | `#E7D9B6` / `#F4ECD9` | hover 底色、表頭、引言 |
| 危險 | `--danger` | `#A5483F` | 刪除（偏磚紅，不用鮮紅） |

**卡片／群組／連結 5 色**（`PALETTE`，key 不變以相容既有資料；solid＝書籤標籤、色票、連結線；light＝卡片底色、群組框底色）：

| key | 名稱 | solid | light | 來源 |
|---|---|---|---|---|
| red | 玫瑰 | `#B06A62` | `#F2DFD9` | 莫內玫瑰 |
| green | 鼠尾草 | `#768C6B` | `#E3E8D8` | 參考圖圓餅「鼠尾草」#A7A386 加深 |
| blue | 灰藍 | `#617A93` | `#DDE4EB` | 參考圖圓餅「灰藍」#A1A2A0／#9CA0A4 |
| orange | 赭石 | `#B07B48` | `#F1E1CC` | 參考圖圓餅「沙色」#ACA394 + 暖化 |
| yellow | 麥稈金 | `#B8954A` | `#F2E8CC` | 參考圖圓餅「金」#D1B07D |

連結預設色＝墨藍 `--edge-c #56657F`；hover＝古金。

### 2.2 字體

| 用途 | 字族（`--f-*`） | 說明 |
|---|---|---|
| 標題（拉丁） | `"Playfair Display"` | 本機 `vendor/fonts/PlayfairDisplay-latin.woff2`（可變字重 400–900，Latin 子集 38 KB）＋ Italic 22 KB；SIL OFL 1.1 |
| 標題（中文） | `"Noto Serif TC UI"` → `Songti TC` → `Noto Serif CJK TC` → `Source Han Serif TC` → `PMingLiU` | 本機 `NotoSerifTC-500-ui-subset.woff2`：只含介面用到的約 700 個字（152 KB）；使用者內容（卡片標題、大綱）缺字時逐字退回系統宋體／明體；SIL OFL 1.1 |
| 介面與內文 | `--f-ui`：系統無襯線（-apple-system / PingFang TC / Noto Sans TC…） | 長文閱讀性優先 |

`--f-display`＝Playfair 優先（數字、英文標題有 Didot 感）；`--f-serif`＝中文襯線優先（側欄字標、知識庫列表、群組標籤、表頭）。

**字級**：側欄字標 17px（字距 .14em）＋ small-caps 標語 11.5px（字距 .2em，金色）；頂列知識庫標題 21px Playfair 400；卡片標題 15px／500；大綱 h1 28px／400、h2 20px、h3 16.5px；內文 14–15px／行高 1.78–1.9；說明 11–12px。標題一律細（400–500），不用粗體。

### 2.3 形狀、細線、陰影

- **圓角**：卡片 8px、選單／彈出層 8px、按鈕 6px、chip／提問列／輸入框 999px（藥丸）、群組框 14px、App 圖示 14/64。
- **細線**：一律 1px（`--hair`）；選取／焦點＝ 1px 古金框＋ 3px `rgba(184,149,74,.20)` 光暈；群組框 1px 虛線。
- **陰影**（暖色、很淡）：`--sh-card` = 內上緣 1px 白光 + `0 1px 2px rgba(70,52,20,.05)` + `0 10px 26px -16px rgba(70,52,20,.28)`；彈出層 `--sh-pop` 更深一級。

### 2.4 圖示

- 自製 inline SVG 細線圖示組（`ICO` / `ico(name, size)`）：24 單位格、**1.4px 線寬**（落在 1.25–1.5 的範圍）、圓頭圓角、`currentColor`、無填色。
- 介面上不再使用 emoji／unicode 符號當圖示（新對話、整理、收合／展開、置中、大綱、調色盤、收合卡片、刪除、複製、設定、連結、開啟、Grok、送出、分支、重新命名、框選、群組、移出群組、重新產生、重設大小、關閉）。舊的符號鍵（例如選單項目的 `'⤡'`）經 `GLYPH_ICO` 對照表轉成 SVG，邏輯不變。
- 顏色：工具列與選單圖示＝ `--gold-deep`；側欄＝ `--gold`；卡片標頭＝ `--muted-2`，hover 變墨藍。
- **知識庫圖示**：使用者選的 emoji 照舊；沒有 emoji 時改為**細線字母章**（透明底、1px 細框，色相由 id 推算後降飽和，框內再一道淡內框，字母用 Playfair）。

### 2.5 點描紋理與光線（Seurat × Monet）

- **點描**：`vendor/textures/pointillism-tile.png`，320×320 無縫磚（Python 產生：約 3400 顆 0.6–1.35px 的點，顏色取金／灰藍／鼠尾草／玫瑰／薰衣草／沙色，透明度 9–23%，量化成 48 色，24 KB）。
- **莫內光**：四層 radial-gradient——右上暖白光、左下灰藍霧、右下鼠尾草霧、四周極淡的暖色暗角。
- 實作在 `#canvas::before`：**螢幕座標、靜態**，不跟著平移縮放，所以只畫一次，不會每格重繪；跟著世界移動的只有原本的點狀格線 `#grid`（顏色改成淡金灰）。效能見 §4。
- 規則：紋理對比要低到「放大看才看得出來」；不要放在卡片、選單、輸入框裡面（閱讀面保持乾淨）。

### 2.6 圖解（Mermaid）與表格

- 清楚的 Claude 式圖解，**不是手繪**：象牙色面板 `#FDFAF3`、1px 細框＋內側 4px 淡金框；標題用 Playfair／宋體，下方 36px 金色細線；節點外框 1.25px 墨藍 `#56657F`；處理節點填淡灰藍 `#DDE4EB`；判斷菱形填淡金 `#EADBB4`；輔助色（cScale）鼠尾草 `#E3E8D8`、玫瑰 `#F2DFD9`、沙色 `#EFE6D3`、薰衣草 `#E4E1EC`；正交（step）連線；標籤字重 500、壓在線上。
- 表格：1px `--hair-2` 外框、6px 圓角、表頭金色淡底＋墨藍宋體。
- 回答提示詞（`prompts/answer-default.md` 與內建預設）已加入這段風格描述；插圖提示詞預設也要求同一種風格（elegant editorial illustration、柔和莫內光、淡淡的修拉點描、奶油色配淡金／灰藍／鼠尾草）。

## 3. 各元件對應

| 元件 | 樣式 |
|---|---|
| 左側欄 | `--sidebar` 底＋左上極淡金光、右下灰藍光；字標「心智圖知識庫」宋體 17px 字距 .14em＋「MINDMAP · KNOWLEDGE」small-caps 金色標語；下方一道金細線；「知識庫」分區標題用字距很寬的 Playfair，右側延伸金細線 |
| 知識庫列表 | 宋體 14.5px 淺色；目前的知識庫＝ 1px 金框、左側 2px 金條、由左往右漸淡的金色底；計數用舊式數字（oldstyle nums） |
| 收合的窄欄 | 同樣深底；知識庫字母章或 emoji 方塊（金細框），目前的那個金框加內框；底部設定圖示 |
| 側欄按鈕 | 透明底、1px 金細框、宋體、金色圖示 |
| 頂列 | 半透明奶油色＋模糊；知識庫標題 21px Playfair；工具列按鈕＝透明底細框＋金色圖示；主要按鈕（大綱）＝炭灰底金字 |
| 畫布 | 奶油色＋點描＋莫內光（§2.5）＋淡金灰點狀格線 |
| 卡片 | 象牙底、1px 米色細線、暖色軟陰影、8px 圓角；標題 Playfair／宋體 15px；選取＝金框光暈；提問泡泡＝細框透明藥丸 |
| chip（延伸問題） | 細框藥丸，hover 淡金底＋金框；「已展開」標籤用 Playfair 斜體金色 |
| 提問列 | 紙色藥丸、淡金框；送出鈕＝炭灰圓鈕、淡金箭頭；提示文字斜體 |
| 群組 | 1px 虛線框＋該色淡底；書籤標籤＝該色實色，宋體白字、字距 .1em |
| 箭頭 | 1.3px 墨藍虛線（6/5）、圓頭；hover 古金 1.9px；選取 2.3px；端點圓點紙色底＋墨藍框；四邊 ＋＝紙色底金框 |
| 右鍵選單／色票 | 象牙底、1px 細線、`--sh-pop`；金色圖示；分區標題宋體金字；色票改圓形 |
| 提示訊息 | 炭灰底、淡金細框、奶油色字；「復原」金色宋體 |
| 大綱側欄 | 像一頁雜誌：紙色底；h1 28px Playfair，下方細線＋ 56px 金色短線；第一段首字放大（drop cap，金色）；h2／h3 墨藍；引言金色左線＋斜體；目錄只用上下細線 |
| 設定／提示詞視窗 | 象牙底；標題 24px Playfair＋金細線；輸入框紙色、聚焦時金框 |
| 圖解／表格 | §2.6 |
| App 圖示 | `icons/option-8.svg`（使用者選定）；備選 option-5／6／7 見 `icons/preview-v2.png` |

## 4. 實作規則

- 新樣式只**覆寫**顏色、字體、細線、陰影；不改 DOM 結構、id、class、`data-*`（測試與程式都依賴它們）。
- 版面計算用到的尺寸不變：卡片寬、標頭高、提問列保留區（44px）、＋ 按鈕與端點圓點的 `--pk` 縮放、調整大小把手。
- 紋理層不能每格重繪：只能用靜態的螢幕座標層，或沿用 `#grid` 的 transform 合成方式。
- 新的介面圖示一律加進 `ICO`（1.4px 線寬，24 單位格）；不要再用 emoji 當介面圖示（使用者自選的知識庫 emoji 除外）。
