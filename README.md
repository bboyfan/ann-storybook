# 📖 Ann Storybook (`ann-storybook`)

**專為 Google Gemini Chat（Canvas）打造的 AI 兒童互動有聲繪本生成技能**

只需在 Gemini Chat 輸入故事靈感、角色或大綱，即可自動企劃 **8～12 頁**（預設 10 頁）符合經典繪本節奏的故事，生成跨頁角色一致的 **3:4 手機直式插圖**，並在雲端沙盒自動組裝成可直接於 **Gemini Canvas** 開啟預覽的互動有聲繪本 Web App。

內建 **Leda（溫柔甜美台灣故事姊姊）** 自然語音朗讀、開書自動預載、段落同步高亮、單手左右滑動翻頁，以及爸媽親自錄音功能。

![角色一致性插圖展示](https://raw.githubusercontent.com/bboyfan/ann-storybook/6e83ada/assets/preview_showcase.jpg)

---

## ✨ 行動端閱讀介面預覽

專為睡前共讀設計的極簡低藍光護眼版面（深可可背景 `#14110F` 搭配羊皮紙柔光文字 `#EDE4D7`），上半部為 `3:4` 滿版大圖、下半部直接連接故事文字卡，右下角僅保留 `🎙️`（語音與爸媽錄音設定）與 `🔊 念故事` 兩顆不干擾畫面的浮動小按鈕：

<p align="center">
  <img src="https://raw.githubusercontent.com/bboyfan/ann-storybook/6e83ada/assets/preview_player.jpg" alt="Ann Storybook 手機播放器介面截圖" width="380" />
</p>

---

## ⚡ 核心特色

1. **經典繪本黃金比例與文筆規範**：
   - 預設 **8～12 頁（標準 10 頁）**，每頁 **2～3 個輕盈短段（全頁 45～65 字）**，兼顧「具體小渴望開場、三次法則與第三次反轉（Rule of Three & Twist）、重複韻律魔法句（Refrain）、具體微動作取代空泛形容詞、圖文分工不寫色票、結尾不說教」。
2. **多元畫風與跨頁角色一致性（`3:4` 直式構圖）**：
   - 支援**使用者自由指定畫風**，或**依故事氛圍自動匹配最適合的繪本媒材**（溫暖透明水彩、粉彩蠟筆、剪紙拼貼、溫潤厚塗 Gouache、溫暖 3D 繪本風）。
   - 採用兩階段 `image_gen:generate_image`（第 1 頁建立主角與畫風基準，第 2～N 頁帶入 `image_references` 平行生成），確保從第一頁到最後一頁角色外觀高度一致。
3. **Leda 台灣自然語音 ＆ 單頁合併連貫朗讀**：
   - 鎖定 `gemini-2.5-flash-preview-tts` 的 **Leda** 溫柔台灣語音，採用單頁合併請求搭配 `temperature: 0.3` 穩定聲線，確保同一頁旁白與對話音色自然連貫不變聲。
   - 開書自動於背景序列預載，支援點擊任意段落跳轉朗讀，以及 `🎙️` 錄下爸媽自己的聲音。
4. **雲端沙盒組裝（省 Token 額度、直接於 Canvas 開啟）**：
   - 在 Gemini 雲端 Python 沙盒內自動完成圖片壓縮（Base64）與模板組裝，不將龐大的 Base64 字串印出至對話視窗，最後透過 `google:show_file` 直接彈出可互動遊玩的繪本卡片。

---

## 🚀 安裝方式（Google Gemini Chat 任務）

請開啟 **Google Gemini Chat（Gemini 任務 / Tasks）**，直接複製以下指令貼入對話框，請 Gemini 幫你完整安裝技能（包含 `SKILL.md` 與 `assets/storybook_template.html` 模板檔）：

```text
請幫我從這個 GitHub 儲存庫完整安裝 ann-storybook 技能（必須同時包含 SKILL.md 以及 assets/storybook_template.html 兩個檔案，缺一不可）：
- 儲存庫連結：https://github.com/bboyfan/ann-storybook
- SKILL.md：https://github.com/bboyfan/ann-storybook/blob/main/SKILL.md
- 繪本模板 HTML：https://github.com/bboyfan/ann-storybook/blob/main/assets/storybook_template.html
```

> 💡 **安裝小提醒**：確認 Gemini 回覆已將 `SKILL.md` 與 `assets/storybook_template.html` 兩個檔案都儲存進 `@ann-storybook` 技能後，開啟一個**新對話**並輸入：
> `@ann-storybook 幫我做一本關於小幽靈找朋友的睡前繪本`
> 即可直接生成並於 Canvas 打開閱讀與聽故事！

---

## 📁 專案結構

```text
ann-storybook/
├── README.md                        # 技能說明書與 Gemini Chat 安裝指南
├── SKILL.md                         # 核心指令（專為 Gemini Chat 原生沙盒與繪本黃金比例設計）
└── assets/
    └── storybook_template.html      # 極簡直式 3:4 有聲繪本模板（Leda 語音＋自動預載＋爸媽錄音）
```

---

## 📄 License

MIT License
