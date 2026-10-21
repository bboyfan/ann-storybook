---
name: ann-storybook
description: Create interactive, mobile-friendly 3D illustrated children's bedtime audio storybooks (HTML web app in Canvas or standalone local HTML with embedded neural zh-TW audio, plus optional printable PDF) with consistent character illustrations, award-winning picture-book prose, visual subplots, page-turn cliffhangers, unified-voice Taiwan Mandarin (zh-TW) narration, automatic page turning, parent voice recording, and offline zh-TW speech fallback. Use when the user mentions "Ann Storybook", asks to create a children's picture book, bedtime story, audio storybook, 有聲繪本, 兒童繪本, 睡前故事, or interactive story web app.
allowed-tools: image_gen google default_api
---

# Ann Storybook (v2.0 — Picture-Book Master Edition)

Build a self-contained, mobile-portrait interactive children's audio picture book (HTML web app) featuring consistent **3:4 vertical** illustrations, authentic award-winning children's picture-book prose (informed by Uri Shulevitz, Matsui Tadashi, Hao Kuang-Tsai, Jon Klassen, Miyanishi Tatsuya, and Hsin-Yi Children's Literature Award standards), unified-voice Taiwan Mandarin (`zh-TW`) narration, swipe/tap page turning, and parent voice recording.

---

## When to Use

- The user invokes `ann-storybook` or asks to create an interactive storybook, bedtime picture book, or children's audio book.

- The user asks for a「有聲繪本」、「兒童繪本」、「睡前故事繪本」or「手機有聲書」on any theme or character.

- The user wants a story with illustrations and natural Taiwan Mandarin (`zh-TW`) read-aloud audio that works smoothly on mobile and desktop browsers.

---

## Steps

### 1. Select Story Archetype, Plan the Arc & Design the Visual Sheet

Before writing a single sentence, choose the best **Story Archetype** for the user's prompt so stories never fall into a repetitive formula.

#### A. The 6 Picture-Book Story Archetypes (六大繪本敘事原型路由器)

Select **1 primary archetype** (or a blend of 2) that best fits the user's outline:

1. **Cumulative & Twist Journey (累加與第三變奏旅途 — e.g., *The Gruffalo*, *The Very Hungry Caterpillar*)**  
   Pages 1–2 launch a concrete micro-quest; Pages 3–6 build a rhythmic pattern across two encounters; **Page 7–8 MUST subvert/twist the pattern on the 3rd encounter** (e.g., the helper now needs help in an unexpected way, or a funny reversal occurs) before the warm payoff on Pages 9–10.

2. **Deadpan Humor & Ironic Counterpoint (冷面幽默與圖文反差 — e.g., Jon Klassen, Yoshitake Shinsuke)**  
   The text stays calm, matter-of-fact, or earnestly absurd (a child's quirky logic or excuse), while the illustrations quietly reveal the funny truth or visual contradiction.

3. **Fierce-Tender Contrast (溫馨反差與鐵漢柔情 — e.g., Miyanishi Tatsuya, Shel Silverstein)**  
   A big, scary, grumpy, or clumsy protagonist meets someone tiny and fearless. A misunderstanding or instinctual tension melts into unexpected tenderness through one disarming action.

4. **Mischief & Safe Return (小調皮越界與安全歸航 — e.g., *Where the Wild Things Are*, Lai Ma)**  
   Escalating sensory play or a relatable childhood tantrum/mess reaches a joyful peak, followed by a quiet moment of vulnerability and a comforting return to warmth and unconditional love.

5. **Try–Fail Escalation & Kid-Logic Breakthrough (嘗試失敗升級與童心破局 — e.g., Mo Willems, Hayashi Akiko)**  
   The protagonist tries 3 increasingly funny/elaborate ways to solve a tiny problem (Attempt 1 fails → Attempt 2 backfires → Attempt 3 hits a funny peak → solved via sideways child-logic).

6. **Sensory Micro-Odyssey & Bedtime Dissolve (微觀漫遊與睡前邊界溶解 — e.g., *Goodnight Moon*, Chen Chih-Yuan)**  
   Slow, poetic close-up exploration of everyday wonders (a puddle, a shadow, a blanket turning into an ocean) that gradually softens in sound, light, and sentence tempo toward sleep.

---

#### B. 5 Master Picture-Book Writing Craft Rules (兒童繪本五大宗師文筆鐵律 — Mandatory)

- **Length & Pacing**: Default to **9 to 13 pages** (ideally **10 pages** unless specified). Write **2 short paragraphs per page** (**40 to 65 Chinese characters total per page**).

1. **Word–Image Counterpoint (圖文對位鐵律：文字絕不重複畫面已知資訊)**  
   - Keep all color palettes, outfits, and static appearance specs strictly inside your internal **Character Visual Sheet**.
   - NEVER write visual prompt descriptions into the story prose (ban phrases describing skin color, hat color, or clothing items that the reader can already see).
   - Text must carry what pictures cannot show: **micro-sensations, inner thoughts, timing, temperature, weight, and humorous contrast**.

2. **Kinetic Verbs & Child-Centric Synesthesia Over Plastic Reduplication (肌肉動詞與童心通感，戒除「塑膠疊字」)**  
   - **Anti-Cliche Ban**: Do NOT stuff pages with generic AI baby-talk reduplications (*圓滾滾、軟綿綿、笑呵呵、亮晶晶、香噴噴、蹦蹦跳跳*). Maximum **1** sound word or reduplication per page, and **never repeat the same onomatopoeia across different pages**.
   - **Kinetic Verbs (肌肉動詞)**: Replace weak adjectives with physical, tactile actions (e.g., instead of *"他很緊張地站在那裡"*, write *"他的腳趾頭緊緊扣住泥巴地，連尾巴尖都不敢晃一下"*).
   - **Child-Centric Metaphors (童心具象比喻)**: Describe sensations using a child's everyday physical world (e.g., *"肚子裡像有小青蛙在敲鼓"*, *"太陽把石頭曬得像剛出爐的烤吐司"*).

3. **Page-Turn Cliffhangers (翻頁懸念動力學 — Pages 1 to 7)**  
   - A picture book is driven by the physical act of turning the page. Do NOT end every page as a closed, self-contained summary.
   - On at least **5 of the first 7 pages**, end the second paragraph with **forward momentum**: an unanswered question, a half-revealed sound/shadow, an interrupted action (`——`), or a sensory teaser that makes the child eager to swipe to the next page.

4. **Rule of Three with a Third-Beat Twist (三段式變奏與反轉)**  
   - If the story uses a recurring chant/refrain or repeated encounter, **the 3rd occurrence must introduce a twist, role reversal, or rhythmic variation** rather than repeating identically three times.
   - Strictly ban adult moralizing or preachy endings (never write *"從此以後他學會了分享/勇敢的道理"*).

5. **Read-Aloud Prosody & Breath Test (松居直「用耳朵看圖」朗讀換氣測試)**  
   - Keep clauses under **12 to 14 characters** between commas. Alternate between crisp **Staccato** short clauses (for surprise, action, or comedy) and gentle **Legato** flowing clauses (for wonder, comfort, and bedtime landing).
   - Strictly ban stiff adult written connectives (*於是、接著、突然間、不僅如此、為了解決這個問題、最後*).

---

#### Prose Craft Comparison (Abstract Examples — Do Not Copy Characters)

- ❌ **Bad (AI Plastic Reduplication + Visual Spec Dump + Flat Summary)**:  
  「藍色毛毛的怪獸波波戴著黃色草帽，肚子餓得咕嚕嚕叫。於是他走到綠油油的院子裡，吃掉軟綿綿又香噴噴的草莓蛋糕，笑呵呵地說太好吃了，真開心！」

- ✅ **Good (Kinetic Verbs + Child Metaphor + Page-Turn Hook)**:  
  「波波的肚皮扁得像一張漏氣的游泳圈，連打個哈欠都聞得到空氣裡的奶油味。  
  他踮起腳尖、屏住呼吸，剛把手指伸進餅乾罐——咦？罐子裡怎麼有一雙圓眼睛正盯著他看？」

---

#### C. Character Visual Sheet, Camera Angles & Visual Subplot (角色設定表、運鏡變化與視覺副線彩蛋)

In your planning notes, define:

1. **Character Visual Sheet**: Exact species/proportions, hex/named colors, signature accessory, and 3D/2D illustration style so every page remains 100% visually consistent.

2. **Camera Angle Progression (運鏡呼吸)**: Vary shot scales across pages—alternate Wide Establishing Shots (遠景), Medium Interaction Shots (中景), Low-Angle Child-Eye Views (幼兒視平線仰角), and Close-Up Emotional Shots (特寫)—so all 10 pages do not share the same flat framing.

3. **Recurring Visual Subplot (跨頁找找看小彩蛋)**: Include a tiny background creature or visual detail (e.g., a tiny ladybug, a sleepy frog, or a floating dandelion seed) that quietly appears in the corner of multiple scenes doing something funny for observant kids to spot.

---

### 2. High-Speed Parallel Illustration Pipeline (極速平行生圖工作流)

Generate portrait-oriented (`3:4`) illustrations with strict character consistency while minimizing total wait time:

1. **Step 2A — Anchor Image (Page 1)**  
   - Generate **Page 1** first (`aspect_ratio="3:4"`) with the full Character Visual Sheet, warm storytelling lighting, and zero text/watermarks.
   - *(Pro Tip: While Page 1 is generating, immediately pre-synthesize all 10 pages of audio in parallel if running in a local environment!)*

2. **Step 2B — Maximum Parallel Fan-Out (Pages 2 to N)**  
   - Once Page 1 is ready, pass the Page 1 image reference (`image_references` / `media_paths`) to **Pages 2 through N**.
   - **Speed Optimization Rule**: Avoid queuing many sequential images inside a single slow worker. In environments supporting subagents or concurrent tool calls, fan out image generation in parallel (e.g., 1 to 2 pages per parallel worker, or simultaneous batch tool calls) so Pages 2–10 complete in a single parallel wave (~60 seconds total) instead of sequential minutes.
   - Never use Python PIL or matplotlib to draw story illustrations.

---

### 3. Compress Illustrations to Base64 Data URLs

Embed all generated images directly into the single-file HTML so the app is 100% self-contained with zero broken external image links:

- Resize/crop each vertical image to `720x960` (`3:4` aspect ratio) JPEG at `quality=80` using Python `PIL.ImageOps.fit(im, (720, 960))` and encode as `data:image/jpeg;base64,...`.

---

### 4. Assemble the Mobile-Portrait Storybook Web App

Use the bundled template at `assets/storybook_template.html` as the base structure:

- Replace `{{STORY_TITLE}}` with the story's title.

- Replace `const PAGES = __PAGES_JSON_PLACEHOLDER__;` with `const PAGES = <JSON_ARRAY>;` (always target the `const PAGES = ...` assignment specifically so comments are never broken by multi-line JSON).

- Always validate the assembled `<script>` block with `node --check` when available.

```json
[
  {
    "pageNum": 1,
    "badge": "1 / 10",
    "title": "Page Title",
    "img": "data:image/jpeg;base64,...",
    "audio": "data:audio/mp3;base64,...",
    "sentences": [
      "First rhythmic paragraph of the page (around 20-32 chars).",
      "Second rhythmic paragraph ending with a page-turn hook (around 20-32 chars)."
    ]
  }
]
```

---

### 5. Dual-Runtime Taiwan Mandarin (`zh-TW`) Audio Engine (Gemini Tasks Canvas + Local Embedded Neural TTS)

Ensure the audio engine in `assets/storybook_template.html` delivers natural human-like Taiwan Mandarin narration in **both** Gemini Web (Gemini Tasks / Canvas) and standalone local browsers:

1. **Mode A — Gemini 2.5 Flash TTS (`gemini-tts`, Default in Gemini Web / Gemini Tasks Canvas)**  
   - Keep `const apiKey = "";` so Gemini Web Canvas automatically injects credentials for `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-tts:generateContent`.
   - Always synthesize both paragraphs of a page together in a single API call (`(PAGES[pageIdx]?.sentences || []).join(" ")`) using the concise prompt `請用溫柔自然的台灣故事媽媽語氣朗讀：${rawText}` and preserve the **7.5-second `Promise.race` timeout + rate-limit cooldown (`ttsCooldownUntil`)** in `assets/storybook_template.html` so Canvas `postMessage` queues never hang on a page.

2. **Mode B — Pre-Synthesized Embedded Neural Audio (`page.audio`, Recommended for Local/Standalone Agent HTML)**  
   - When running in a local CLI/IDE environment (such as Antigravity), concurrently synthesize all pages in parallel using `asyncio.gather` with `edge-tts` (`voice="zh-TW-HsiaoChenNeural"`, `rate="-4%"`) or Gemini TTS API (if `GEMINI_API_KEY` is present), and embed the resulting `data:audio/mp3;base64,...` string directly into `page.audio`.
   - This guarantees **instant, zero-latency playback** with a warm, natural Taiwan story-mother voice across any browser or mobile device without requiring the user to enter an API key.

3. **Mode C — Parent Voice Recording (`parent-record`) & Offline Web Speech Fallback (`web-speech`)**  
   - Parents can record their own voice per page via `MediaRecorder` or import an audio file, which automatically takes top priority.
   - Offline Web Speech fallback scores system voices (`scoreTaiwanVoice`) to lock onto `zh-TW` voices (`Mei-Jia`, `HsiaoChen`, `Google 國語（臺灣）`).

---

### 6. Save and Present

- **In Gemini Web / Gemini Tasks Canvas**: Write the completed HTML file to `/working_dir/<conversation_id>/artifacts/file_generation/ttl=63d/output/<Story_Title>_手機有聲繪本.html` and call `google:show_file`.

- **In Local Antigravity / CLI**: Save the self-contained HTML file to the active workspace or `/Users/bboyfan/Downloads/<Story_Title>_手機有聲繪本.html` and open it in the browser (`open "<path>"`).

- If the user also requests a printable PDF picture book, generate a matching PDF using ReportLab with embedded Chinese fonts.
