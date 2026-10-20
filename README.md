# 📖 Ann Storybook (`ann-storybook`)

**AI 兒童睡前互動有聲繪本生成技能（Agent Skill）**

只需輸入簡單的故事大綱或主題，即可自動企劃分鏡、生成具備高度角色一致性的 **3:4 手機直式插圖**，並封裝成 **100% 獨立運作的單一 HTML5 有聲繪本 Web App**。

支援台灣國語（`zh-TW`）自然語音朗讀、句段同步高亮、點擊指定段落跳讀、單手滑動翻頁，以及爸媽親自錄音功能。

![角色一致性插圖展示](assets/preview_showcase.jpg)

---

## ✨ 行動端閱讀介面預覽

專為睡前共讀打造的夜間低藍光護眼介面（深可可暖黑背景 `#14110F` 搭配羊皮紙柔光文字 `#EDE4D7`）：

<p align="center">
  <img src="assets/preview_player.jpg" alt="Ann Storybook 手機播放器介面截圖" width="380" />
</p>

---

## 🌟 執行環境與語音體驗說明（必讀）

本技能遵循開放的 `SKILL.md` 標準，可在 **Google Gemini 網頁版（Gemini 任務 / Gemini Chat）** 以及 **本機端 AI Agent（Antigravity / Claude Code / Gemini CLI）** 執行。

不同環境在「語音模型串接」上有以下核心差異：

### 1. Google Gemini 網頁版（Gemini 任務 / 前身為 Gemini Spark）— 🏆 最完整原生體驗

在 Gemini 網頁版透過 **Gemini 任務（Tasks，前身為 Gemini Spark）** 或在對話中透過 `/` 呼叫此 Skill，是目前**最完整的開箱即用體驗**：

- **直接串接 Gemini 語音模型**：網頁版沙盒會自動注入雲端授權憑證，直接呼叫 **Gemini 2.5 Flash TTS (`gemini-tts`)**。

- **免填 API Key**：不需自行申請或設定任何金鑰，即可即時合成聲線統一、自然溫柔的「台灣故事媽媽（Kore）」語音。

- **即時互動與下載**：任務完成後可直接在畫面右側 Canvas 預覽翻頁、點選句子朗讀，並支援一鍵下載每頁的 `.wav` 語音檔。

---

### 2. 本機端 AI Agent（Antigravity / Claude Code / Gemini CLI）— 💻 預錄自然語音內嵌

當你在本機端 Agent 執行此 Skill 並直接用本機瀏覽器（Chrome / Safari）打開產出的 `.html` 檔時，由於脫離了 Gemini 網頁版的雲端容器，預設無法自動帶入雲端憑證，若直接播放會退回系統內建的機械音（`Web Speech API`）。

**在本機端獲得真人自然語音的 3 種方式：**

1. **本機預先合成自然語音並嵌入 HTML（最推薦）**  
   在執行任務時，讓本機 Agent 先透過 Python 併發呼叫神經網路語音模型（例如 `edge-tts` 的 `zh-TW-HsiaoChenNeural` 台灣故事媽媽聲線，或使用你的 `GEMINI_API_KEY`），在數秒內將 10 頁語音轉為 Base64 嵌入 `PAGES[i].audio` 欄位中。  
   👉 **優點**：產出的單一 HTML 檔案**完全免填 Key、免聯網、點開秒播真人語音**，直接傳到手機或 LINE 也能原音重現。

2. **在繪本播放器內填入 Gemini API Key**  
   點擊繪本畫面右下角 `🎙️` 按鈕 → 展開「進階選項」→ 在「選填 Gemini API Key」貼入金鑰，即可在本機瀏覽器即時呼叫 Gemini 2.5 Flash TTS。

3. **爸媽親自錄音（`MediaRecorder`）或匯入音檔**  
   點擊右下角 `🎙️` 按鈕，直接用手機或電腦麥克風為每一頁錄下爸爸媽媽的聲音，播放器會自動優先播放爸媽錄音。

---

### 雙環境功能對照表

| 比較項目 | 🌟 Gemini 網頁版（Gemini 任務 / Spark） | 💻 本機端 Agent（Antigravity / CLI） |
| :--- | :--- | :--- |
| **體驗完整度** | **最完整的雲端一條龍體驗（首選）** | **適合封裝為永久離線單一檔案、跨裝置分享** |
| **預設語音來源** | 直接連線 **Gemini 2.5 Flash TTS** | 建議由本機 Agent **預先合成自然語音嵌入 HTML** |
| **API Key 需求** | **免填 Key**（雲端沙盒自動授權） | 預先嵌入音檔則免填 Key；若要即時連線則需填 Key |
| **生圖加速策略** | 雲端沙盒依序生成 | 支援多 Subagent **平行扇出（Parallel Fan-out）** 極速生圖 |

---

## 🎨 核心創作特色（v2.0 繪本宗師版）

本技能整合歐美與日台繪本大師（Uri Shulevitz、松居直、郝廣才、Jon Klassen、宮西達也、吉竹伸介）的創作理論，徹底破除 AI 寫作常見的「流水帳」與「塑膠疊字」：

### 1. 六大經典繪本敘事原型路由器

不再每本故事都走一成不變的公式，Agent 會依主題自動匹配最適合的敘事結構：

- **累加與第三變奏旅途（Cumulative & Twist）**：前兩次建立韻律預期，第三次遭遇必定發生幽默反轉或角色互換。

- **冷面幽默與圖文反差（Deadpan & Counterpoint）**：文字一本正經胡說八道，插畫卻默默透露相反真相（吉竹伸介 / Jon Klassen 風）。

- **溫馨反差與鐵漢柔情（Fierce-Tender Contrast）**：巨大或看似兇猛的主角遇上天真小不點，在誤會中展現溫柔守護（宮西達也風）。

- **小調皮越界與安全歸航（Mischief & Safe Return）**：感官玩耍或情緒大爆發後，回到溫暖安全的懷抱（《野獸國》/ 賴馬風）。

- **嘗試—失敗升級與童心破局（Try–Fail Escalation）**：三次越來越誇張的嘗試，最後用兒童奇想意外解決問題。

- **微觀漫遊與睡前邊界溶解（Sensory Bedtime Dissolve）**：放慢腳步凝視日常微小奇蹟，語調與光線隨頁數漸柔入眠（《月亮晚安》風）。

---

### 2. 五大繪本宗師文筆鐵律

- **圖文對位（不贅述畫面設定）**：角色色票與服裝嚴格鎖在生圖設定表（Character Visual Sheet），內文絕不寫出畫面一眼可見的顏色與外觀，專注描寫**聲音、溫度、重量與微動作**。

- **肌肉動詞與童心通感比喻**：禁用「圓滾滾、軟綿綿、笑呵呵」等廉價 AI 疊字，改用具體動作與幼兒日常比喻（如：「露珠像爆米花一樣跳起來」、「肚皮扁得像漏氣的游泳圈」）。

- **翻頁懸念動力學（Page-Turn Cliffhangers）**：前段跨頁結尾埋入未知聲響、疑問或未完動作（`——`），吸引孩子主動滑向下一頁。

- **松居直「用耳朵看圖」朗讀換氣測試**：每頁嚴格控制在 2 短段（共 40–65 字）、逗號間不超過 12–14 字，朗讀流暢不喘氣。

---

## 📦 安裝方式

### 方式一：在 Google Gemini 網頁版（Skills / Gemini 任務）使用

Google 已將舊版 Gems 全面升級為 **Skills（技能）** 與 **Gemini 任務（Tasks，前身為 Gemini Spark）**：

1. 下載本儲存庫（包含 [`SKILL.md`](SKILL.md) 與 [`assets/storybook_template.html`](assets/storybook_template.html)）。

2. 在 Gemini 網頁版左側選單進入「**技能（Skills）**」建立或匯入此技能資料夾。

3. 在 **Gemini 任務（Tasks）** 或一般對話中輸入 `/ann-storybook`（或直接描述想做的有聲繪本），即可自動執行並在 Canvas 中開啟互動有聲繪本。

---

### 方式二：在 Antigravity / Claude Code / Gemini CLI 安裝

將本儲存庫 Clone 至本機全域 Skills 目錄即可自動載入：

```bash
# Antigravity / Gemini CLI
git clone https://github.com/bboyfan/ann-storybook.git ~/.gemini/config/skills/ann-storybook

# Claude Code
git clone https://github.com/bboyfan/ann-storybook.git ~/.claude/skills/ann-storybook
```

---

## 💡 推薦提示詞範本（可直接複製使用）

### 範本 1：經典溫馨冒險（適合 Gemini 任務 / 網頁版直接使用）

```text
請使用 ann-storybook 技能，幫我製作一本 10 頁的 3D 動畫風格睡前有聲繪本：

- 主題：怕黑的小燈籠魚泡泡，今晚頭頂的發光球突然「啪」一聲熄滅了，它必須在深海珊瑚鎮找回亮光。
- 敘事風格：採用「嘗試—失敗升級與童心破局」原型，文字要有豐富的動作細節與翻頁懸念，不要使用老套疊字。
```

---

### 範本 2：宮西達也式「鐵漢柔情反差風」

```text
請用 ann-storybook 製作一本 10 頁兒童有聲繪本：

- 主題：森林裡最愛生氣、嗓門像打雷一樣大的大棕熊，意外撿到一顆一直跟著他滾的小松果，裡面鑽出一隻完全不怕他、還把他大肚子當彈跳床的小睡鼠。
- 敘事風格：採用「溫馨反差與鐵漢柔情（Fierce-Tender Contrast）」原型。
- 視覺風格：厚塗繪本水彩結合立體光影，每一頁角落請藏一隻戴著橡果帽的小青蛙當作給孩子的「找找看」視覺彩蛋。
```

---

### 範本 3：吉竹伸介 / Jon Klassen 式「冷面幽默與童言童語風」

```text
請用 ann-storybook 製作一本 10 頁互動有聲繪本：

- 主題：小橘貓阿布打翻了桌上的牛奶杯，但他一本正經地向剛走進廚房的媽媽推理「為什麼這絕對是外星章魚幹的好事」。
- 敘事風格：採用「冷面幽默與圖文反差（Deadpan Humor & Counterpoint）」原型，文字要一本正經地胡說八道，但畫面要悄悄露出阿布鬍鬚上沾滿牛奶的破綻！
```

---

### 範本 4：本機端 Agent 專用（平行極速生圖＋預先合成台灣自然語音嵌入）

> 若你在 **Antigravity / 本機 CLI** 執行，使用此提示詞可讓 Agent 直接把台灣故事媽媽自然語音預錄並嵌入 HTML 中：

```text
請使用 ann-storybook 技能製作一本 10 頁的 3D 繪本：

- 故事大綱：巨大恐龍在郊遊，和好朋友一起去爬山，認識了好多新朋友，最後在山頂看星星野餐。
- 畫風：溫暖 3D 皮克斯動畫風格。
- 本機執行要求：請使用平行扇出（Parallel Fan-out）加速生成第 2~10 頁插圖，並在本機使用 edge-tts (zh-TW-HsiaoChenNeural) 併發合成 10 頁台灣故事媽媽自然語音直接內嵌至 HTML 的 page.audio 中，完成後幫我打開 HTML。
```

---

## 📁 專案結構

```text
ann-storybook/
├── README.md                        # 技能說明書、雙環境語音指南與提示詞範本
├── SKILL.md                         # v2.0 繪本宗師版核心指令（6大敘事原型＋5大文筆鐵律＋平行工作流）
└── assets/
    ├── storybook_template.html      # 行動端直式 3:4 有聲繪本播放器模板（支援 Canvas TTS / 內嵌音訊 / 爸媽錄音）
    ├── preview_player.jpg           # 行動端閱讀器畫面截圖
    └── preview_showcase.jpg         # 跨頁角色一致性插圖展示
```

---

## 📄 License

MIT License
