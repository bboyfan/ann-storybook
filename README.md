# 📖 Ann Storybook (`ann-storybook`) — AI 互動有聲繪本生成技能

**Ann Storybook** 是一套專為 AI Agent 與 Gemini Canvas 設計的**兒童睡前互動有聲繪本生成技能（Skill）**。只需輸入簡單的故事大綱或主題，即可自動企劃分鏡、生成具備高度角色一致性的 **3:4 手機直式插圖**，並封裝成 **100% 獨立運作的單一 HTML5 有聲繪本 Web App**（支援台灣國語 `zh-TW` 自然語音朗讀、段落同步高亮、點擊指定段落朗讀、單手滑動翻頁，以及爸媽親自錄音功能）。

![角色一致性插圖展示](assets/preview_showcase.jpg)

---

## ✨ 畫面預覽（行動端夜間護眼閱讀介面）

<p align="center">
  <img src="assets/preview_player.jpg" alt="Ann Storybook 手機播放器介面截圖" width="380" />
</p>

---

## 🎯 核心特色（v2.0 繪本宗師版）

### 1. 融合國際與日台繪本大師的寫作理論
不再產出千篇一律的 AI 流水帳或滿篇「圓滾滾、軟綿綿、笑呵呵」的塑膠兒語。內建 **6 大經典童話繪本敘事原型路由器** 與 **5 大宗師文筆鐵律**：
- **圖文對位（Word–Image Counterpoint）**：遵循凱迪克金獎大師 Uri Shulevitz《繪本之力》原則，所有外觀色票與服裝設定嚴格鎖在生圖專用表（Character Visual Sheet），內文絕不重複畫面已知資訊，專注描寫**聲音、溫度、重量、微動作與心理反差**。
- **肌肉動詞與童心通感比喻**：戒除廉價疊字，改用具體身體感知與幼兒日常具象比喻（例如用「肚皮扁得像漏氣的游泳圈」、「露珠像爆米花一樣跳起來」取代抽象形容詞）。
- **翻頁懸念動力學（Page-Turn Cliffhangers）**：前段跨頁結尾自動埋入未知聲響、問題或未完動作（`——`），引誘孩子主動滑向下一頁。
- **松居直「用耳朵看圖」朗讀換氣測試**：每頁精準控制在 2 短段（40–65 字）、每個逗號間不超過 12–14 字，斷奏（Staccato）與圓滑奏（Legato）交錯，父母與 AI 朗讀皆自然不費力。

### 2. 跨頁角色一致性與運鏡呼吸
- 先生成第 1 頁作為**角色基準母圖（Anchor Reference）**，後續頁面皆以母圖進行一致性約束，並自動交錯遠景、中景、幼兒視平線仰角與特寫鏡頭。

### 3. 專為睡前共讀打造的行動端播放器
- **夜間低藍光配色**：採用深可可暖黑背景（`#14110F`）搭配羊皮紙柔光文字（`#EDE4D7`），關燈共讀不刺眼。
- **句段同步高亮與點選跳讀**：朗讀時自動依字數比例高亮當前段落；點擊任一段落即可從該句開始播放。
- **靜音共讀 vs. AI 連播雙模式**：未開啟語音時手動滑動翻頁保持安靜（方便爸媽自己念）；開啟「🔊 念故事」後則會自動朗讀並翻頁。

---

## 🔊 執行環境與語音模型完整指南（重要）

本技能支援在 **Google Gemini 網頁版（Gemini Chat / Canvas）** 以及 **本機端 AI Agent（Antigravity / Claude Code / Gemini CLI）** 運行，兩者在語音合成機制上有重要差異：

| 比較項目 | 🌟 Google Gemini Chat（網頁版 Canvas） | 💻 本機端 Agent（Antigravity / CLI） |
| :--- | :--- | :--- |
| **體驗完整度** | **最完整的開箱即用雲端體驗（推薦首選）** | **最適合封裝為永久離線單一檔案、免金鑰分享** |
| **預設語音引擎** | 直接連線 **Gemini 2.5 Flash TTS (`gemini-tts`)** | 預設離線瀏覽器無雲端權杖，**建議由本機 Agent 預先合成自然語音嵌入 HTML** |
| **API Key 需求** | **免填 Key**（Gemini Canvas 沙盒會自動注入憑證） | 若未預先內嵌音檔，需在播放器填入 Gemini API Key，否則會降級為系統內建機械音 |
| **最佳實踐** | 生成後直接在右側 Canvas 預覽並點擊「🔊 念故事」 | 生成時讓本機 Agent 併發合成自然語音寫入 `page.audio`（Base64），點開即播真人語音 |

### 為什麼會有這個差異？
1. **在 Gemini Chat 網頁版執行時**：
   模板中的 `const apiKey = "";` 在 Gemini Web Canvas 預覽環境內，會由 Google 自動注入當下對話的授權憑證，直接呼叫 `gemini-2.5-flash-preview-tts` 模型，即時合成統一聲線的**台灣故事媽媽（Kore 聲線）**，並在背景自動預載下一頁。
2. **在本機端 Agent（如 Antigravity）執行時**：
   當你從本機直接用 Chrome / Safari 打開獨立的 `.html` 檔時，因為脫離了 Gemini 網頁版的 Canvas 容器，空字串 `apiKey` 無法直接通過 Google API 驗證，播放器會自動降級到第三層備援（`Web Speech API` 系統內建機械音）。
   - **✅ 本機端最佳解法（預先合成內嵌）**：在請本機 Agent 製作繪本時，直接讓 Agent 在本機透過 Python 併發呼叫神經網路語音（例如 `edge-tts` 的 `zh-TW-HsiaoChenNeural` 台灣故事媽媽聲線，或使用你的 `GEMINI_API_KEY`），在 4 秒內把 10 頁語音轉為 Base64 直接寫進 `PAGES[i].audio` 欄位中。這樣產出的 HTML **完全不需聯網、免填 API Key，傳到手機或 LINE 打開都是 100% 真人級自然語音！**
   - **✅ 播放器內建錄音與手動 Key**：你也可以隨時點擊畫面右下角的 `🎙️` 按鈕，直接用麥克風錄下爸媽自己的聲音，或在「進階選項」貼入自己的 Gemini API Key。

---

## 📦 安裝與使用方式

### 方式一：在 Google Gemini 網頁版使用
1. 下載本專案的 [`SKILL.md`](SKILL.md) 與 [`assets/storybook_template.html`](assets/storybook_template.html)。
2. 在 Gemini 建立自訂 Gem 或上傳檔案至對話中，輸入下方提示詞即可直接在 Canvas 生成並聆聽。

### 方式二：在 Antigravity / Claude Code / Gemini CLI 安裝為全域技能
將本儲存庫 Clone 至你的全域 Skills 目錄：

```bash
# Antigravity / Gemini CLI
git clone https://github.com/bboyfan/ann-storybook.git ~/.gemini/config/skills/ann-storybook

# Claude Code
git clone https://github.com/bboyfan/ann-storybook.git ~/.claude/skills/ann-storybook
```

---

## 💡 推薦提示詞範本（Ready-to-Use Prompts）

下載或啟用本技能後，你可以直接複製以下提示詞來生成不同風格的有聲繪本：

### 範本 1：經典溫馨冒險（適合 Gemini Chat 網頁版直接使用）
```text
請使用 ann-storybook 技能，幫我製作一本 10 頁的 3D 動畫風格睡前有聲繪本：
- 主題：怕黑的小燈籠魚泡泡，今晚它的發光球突然「啪」一聲熄滅了，它必須在深海珊瑚鎮找回亮光。
- 敘事風格：採用「嘗試—失敗升級與童心破局」原型，文字要有豐富的動作細節與翻頁懸念，不要使用老套疊字。
```

### 範本 2：宮西達也式「鐵漢柔情反差風」
```text
請用 ann-storybook 製作一本 10 頁兒童有聲繪本：
- 主題：森林裡最愛生氣、嗓門像打雷一樣大的大棕熊，意外撿到一顆一直跟著他滾的小松果，裡面鑽出一隻完全不怕他、還把他大肚子當彈跳床的小睡鼠。
- 敘事風格：採用「溫馨反差與鐵漢柔情（Fierce-Tender Contrast）」原型。
- 視覺風格：厚塗繪本水彩結合立體光影，每一頁角落請藏一隻戴著橡果帽的小青蛙當作給孩子的「找找看」視覺彩蛋。
```

### 範本 3：吉竹伸介 / Jon Klassen 式「冷面幽默與童言童語風」
```text
請用 ann-storybook 製作一本 10 頁互動有聲繪本：
- 主題：小橘貓阿布打翻了桌上的牛奶杯，但他一本正經地向剛走進廚房的媽媽推理「為什麼這絕對是外星章魚幹的好事」。
- 敘事風格：採用「冷面幽默與圖文反差（Deadpan Humor & Counterpoint）」原型，文字要一本正經地胡說八道，但畫面要悄悄露出阿布鬍鬚上沾滿牛奶的破綻！
```

### 範本 4：本機端 Agent 專用（極速平行生圖＋自動內嵌台灣自然語音）
> 若你在 **Antigravity / 本地 CLI** 使用，加上最後一句即可讓 Agent 直接把自然語音打包進 HTML：
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

## 📄 License
MIT License
