# 📖 Ann Storybook (`ann-storybook`)

**AI 兒童互動有聲繪本生成技能（極速省 Token 優化版）**

只需輸入故事大綱、角色想法或主題，即可自動規劃 **8～12 頁**完整故事（每頁 **3～4 段豐富敘事**）、以兩階段平行生成具備高度角色一致性的 **3:4 手機直式插圖**，並透過 Python 黑盒封裝成 **100% 獨立運作的單一 HTML5 有聲繪本 Web App**。

內建單一鎖定 **Leda（溫柔甜美台灣故事姊姊）** AI 語音、全自動背景佇列預載、0 秒內建台灣語音秒播切換、段落同步高亮、單手滑動翻頁，以及爸媽親自錄音功能。

![角色一致性插圖展示](https://raw.githubusercontent.com/bboyfan/ann-storybook/6e83ada/assets/preview_showcase.jpg)

---

## ✨ 行動端閱讀介面預覽

專為睡前共讀打造的夜間低藍光護眼介面（深可可暖黑背景 `#14110F` 搭配羊皮紙柔光文字 `#EDE4D7`）：

<p align="center">
  <img src="https://raw.githubusercontent.com/bboyfan/ann-storybook/6e83ada/assets/preview_player.jpg" alt="Ann Storybook 手機播放器介面截圖" width="380" />
</p>

---

## ⚡ 核心架構與優化亮點

1. **Python 黑盒封裝（杜絕 Base64 暴增 Token）**：
   - 插圖縮放（`600x800`, JPEG Q75）、Base64 編碼與 HTML 模板合成 100% 在單一 Python 腳本內直接讀寫檔案完成，不將 Base64 印出至終端或傳入對話上下文，節省 85%～90% Token 消耗。

2. **兩階段平行生圖（Parallel Tool Calls + `image_references`）**：
   - 第一階段（Turn A）生成第 1 頁基準圖；第二階段（Turn B）在同一回合平行生成第 2～N 頁並帶入 `image_references=[第1頁]`，後續提示詞僅需描述當頁動作與場景變化。

3. **8～12 頁完整故事 ＆ 每頁 3～4 段豐富層次**：
   - 預設規劃 **8～12 頁**，每頁包含 **3～4 個段落（約 65～110 字）**，兼顧動作細節、角色對話與翻頁好奇心。
   - 支援**自由指定畫風**或**依故事氣質自動匹配畫風**（溫暖透明水彩、粉彩蠟筆、剪紙拼貼、厚塗不透明水彩、溫暖黏土/3D）。

4. **單一鎖定 Leda 台灣語音 ＆ 智慧背景佇列預載**：
   - 統一採用 **Leda** 溫柔甜美聲線，透過全域單線程佇列（`ttsQueueChain`）依序背景預載，不塞車、不觸發併發限流。
   - 主畫面右下角提供 `✨ AI語音 / ⚡ 內建秒播` 一鍵切換，以及 `🎙️` 爸媽親自錄音功能。

---

## 📦 安裝方式

### 方式一：在 Google Gemini 網頁版（技能 / Gemini 任務）匯入

1. 直接上傳打包好的 `ann-storybook.zip`（內僅含 [`SKILL.md`](SKILL.md) 與 [`assets/storybook_template.html`](assets/storybook_template.html)，無多餘二進位圖片或隱藏檔）。
2. 在 **Gemini 任務（Tasks）** 或對話中輸入故事大綱即可開始製作。

---

### 方式二：在 Antigravity / Claude Code / Gemini CLI 安裝

```bash
# Antigravity / Gemini CLI
git clone https://github.com/bboyfan/ann-storybook.git ~/.gemini/config/skills/ann-storybook

# Claude Code
git clone https://github.com/bboyfan/ann-storybook.git ~/.claude/skills/ann-storybook
```

---

## 📁 專案結構

```text
ann-storybook/
├── README.md                        # 技能說明書與安裝指南
├── SKILL.md                         # 核心指令（Python 黑盒省 Token＋兩階段平行生圖＋8-12頁豐富敘事）
└── assets/
    └── storybook_template.html      # 行動端直式 3:4 有聲繪本播放器模板（Leda 語音＋佇列預載＋秒播切換）
```

---

## 📄 License

MIT License
