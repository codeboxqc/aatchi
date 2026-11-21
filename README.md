 # AATCHI! — Living Cartoon Desktop Companion

> A standalone interactive Windows desktop companion & `.avatar` player built in native **C++20, SDL3, OpenGL 3.3, Dear ImGui, FFmpeg, and Win32 API**.  
> 100% compatible with **Dance Avatar Studio** (`.avatar` ZIP bundles).

🌐 **Videos, Community Packs & `.avatar` Downloads:** **[https://nutz.club](https://nutz.club)**

---

## 🎬 Showcase Videos & `.avatar` Downloads

Visit **[nutz.club](https://nutz.club)** to:
- Watch live **preview videos** (`.webm`) of AATCHI characters in action
- Download ready-to-use **`.avatar`** character bundles
- Follow the **A-to-Z Transparent Video Guide** to turn green-screen (`#00FF00`) AI clips into transparent `.webm` animations for `editor.exe`

---

## ✨ Highlights

| Feature | Details |
| :--- | :--- |
| **38+ Animated Actions** | 14 Basic, 7 Interactive, 7 Daily Activity, and 10 Emotion slots |
| **26 Desktop Hijinks** | Includes 3 rare **12% Jackpot Events** (UFO Abduction Beam, Ninja Smoke Bomb, Super Power-Up Aura) |
| **60 Comic Starbursts** | Classic 1966/1980s jagged comic pop-ups (`POW!`, `BOING!`, `KAPOW!`, `YEET!`, `BWAHAHA!`) |
| **240+ Retro LCD Quips** | Phosphor-green `LCD // 14400` ticker with hilarious desktop, gaming, and work quips |
| **Desktop Physics** | Window platforming, desktop icon / Recycle Bin detection (UI Automation), 4-way gravity falls, and multi-monitor roaming |
| **5 GPU Render FX** | Right-click shaders: Strobe Flash, Rainbow Color, Neon RGB Glitch, Golden Aura, Hologram Shimmer |
| **13 Anime Backdrops** | 10-second dramatic FX including Matrix Rain, Mech HUD, Neon Synthwave, Black Hole Warp, Akira Neo-Tokyo, Flame Aura, and Plasma Anime |
| **Smart PC Awareness** | Reacts to 10 Windows hotkeys (`Ctrl+C/V/Z/S/X/A/F`, `Alt+Tab`, `Alt+F4`, `Ctrl+Alt+Del`), **WASAPI** audio beat dancing, battery/charging alerts, hourly clock & date banners |
| **Retro Synth & Voices** | **36** procedural in-memory cartoon/arcade SFX, **75** funny SAPI voice lines, and an ephemeral sunset-gradient live typing ticker (never saved) |
| **Kid-Safe AI Brain** | Optional non-blocking WinHTTP multi-provider chat (**Groq, xAI Grok, Google Gemini, OpenAI ChatGPT**) with BYO keys, round-robin failover, self-healing `/models` fetch, and 180-char frosted ice-blue replies |

---

## 📦 Using `.avatar` Files

1. Download any `.avatar` bundle from **[nutz.club](https://nutz.club)**.
2. Launch **`AATCHI.exe`**.
3. Drag and drop the `.avatar` file onto AATCHI (or load it from the system tray menu).

---

## 🆓 Free Edition vs. 🚀 AATCHI PRO ($0.99 One-Time)

### Free Edition (`$0` Forever)
- Up to **3 bundled official avatars** (`AATCHI.avatar`, `liberty.avatar`, `Yo.avatar`)
- Full standalone transparent Win32 desktop player & click-through mode
- All 60 comic bursts, 240+ LCD quips, 26 hijinks, 5 GPU FX, 13 anime backdrops, 36 synth SFX, 75 voices, and optional BYO-key AI chat

### AATCHI PRO (`$0.99` One-Time on Microsoft Store)
- **Unlimited Avatars** — load 10, 50, or 500+ community `.avatar` packs from **[nutz.club](https://nutz.club)**
- **4 Bonus Character Addons** included immediately
- **Auto-Rotation Modes** — automatically swap to a random avatar every 4 hours or daily
- **Full AATCHI-Editor Studio (`editor.exe`)**:
  - Import transparent `.WebM`, animated `.WebP`, and `.MP4` videos
  - Live Chroma/Luma Key green/black screen remover & eyedropper
  - Frame Cropper, Loop Trimmer, 38+ action slots, and 1-click `.avatar` ZIP export

---

## ⚙️ Native Tech Stack & Source Files

**Built with:** `C++20` • `SDL3` • `OpenGL 3.3 Core` • `Dear ImGui` • `FFmpeg` • `miniz` • `WinHTTP` • `Win32 / DWM` • `WASAPI` • `UI Automation` • `SAPI TTS` • `BCrypt SHA-256`

- `avatar_desktop_main.cpp` — Entry point (`AATCHI.exe`), SDL3 + OpenGL 3.3 transparent DWM window, 36-sound `SynthAudioPlayer`, Win32 tray & ImGui menu, `SafeDesktopObstacleScanner`, `Win32ContextMonitor`
- `companion_engine.h` — Core types (`AnimState`, `ActionPriority`, `RetroSfxId`, `SpecialHijinkKind`, `BgAnimeKind`, `RenderFxKind`, `CompanionSettings`, `CompanionEngine`)
- `companion_engine.cpp` — State machine, 38-action catalog, shuffle bag, 60 comic bursts, 240+ LCD quips, 75 SAPI voice lines, 4-way gravity & obstacle physics, GPU FX
- `ai.h` — Thread-safe `AiChatEngine`, `AiConfig`, and `AiReply` interface
- `ai.cpp` — Non-blocking WinHTTP HTTPS client (Groq, xAI Grok, Gemini, ChatGPT), kid-safe guardrails, 100 built-in desktop questions, and self-healing `/models` fallback

---

## 🛡️ Privacy & Safety

- **Zero Spyware / Zero Ads**
- **Ephemeral Live Typing:** Typing ticker reactions are never logged or saved
- **Kid-Safe AI Prompting:** Built-in safety filter and clean 180-character responses

---

## 🔗 Links

- **Videos & `.avatar` Packs:** [https://nutz.club](https://nutz.club)
