<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>AATCHI! — Living Cartoon Desktop Companion</title>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Bangers&family=Fredoka:wght@400;600;700&family=JetBrains+Mono:wght@500;700&display=swap" rel="stylesheet" />
<style>
  :root {
    --y: #FFE135; --c: #33E1FF; --p: #FF4DA6; --l: #52FA7A; --o: #FF8A1E; --v: #9B5DE5;
    --cream: #FFFDF5; --soft: #FFF7DC; --ink: #161622; --ink2: #2D2D44;
    --b: 3px solid var(--ink); --sh: 5px 5px 0 var(--ink);
    --f-comic: 'Bangers', Impact, cursive, sans-serif;
    --f-body: 'Fredoka', 'Segoe UI', system-ui, sans-serif;
    --f-mono: 'JetBrains Mono', Consolas, monospace;
  }
  *, *::before, *::after { box-sizing: border-box; max-width: 100%; }
  html, body {
    margin: 0; padding: 0; width: 100%; overflow-x: hidden;
    scroll-behavior: smooth; font-family: var(--f-body); color: var(--ink);
    background-color: #FFF6C8;
    background-image: radial-gradient(rgba(22,22,34,.1) 1.5px, transparent 1.5px);
    background-size: 20px 20px; line-height: 1.5;
  }
  a { color: inherit; text-decoration: none; }
  button { font-family: var(--f-body); cursor: pointer; }
  .wrap { width: 100%; max-width: 760px; margin: 0 auto; padding: 12px; display: flex; flex-direction: column; gap: 22px; }
  .col { display: grid; grid-template-columns: 1fr; gap: 14px; width: 100%; }

  /* Header */
  .topbar {
    background: var(--y); border: var(--b); border-radius: 18px; box-shadow: var(--sh);
    padding: 12px 14px; display: flex; flex-direction: column; align-items: center; gap: 10px;
  }
  .logo {
    display: inline-flex; align-items: center; gap: 8px; background: var(--p); color: #fff;
    padding: 5px 16px; border: var(--b); border-radius: 999px; box-shadow: 3px 3px 0 var(--ink);
    font-family: var(--f-comic); font-size: 1.65rem; letter-spacing: 1.5px; text-shadow: 2px 2px 0 var(--ink);
  }
  .dot { width: 12px; height: 12px; background: var(--y); border: 2px solid var(--ink); border-radius: 50%; }
  .nav { display: flex; flex-wrap: wrap; justify-content: center; gap: 7px; width: 100%; }
  .nav a {
    font-weight: 700; font-size: .85rem; padding: 6px 12px; background: var(--cream);
    border: 2.5px solid var(--ink); border-radius: 999px; box-shadow: 2px 2px 0 var(--ink);
  }
  .nav a:hover { background: var(--c); }
  .nav a.pro-link { background: var(--l); }

  /* Shared Cards & Buttons */
  .card {
    background: var(--cream); border: var(--b); border-radius: 20px;
    box-shadow: var(--sh); padding: clamp(16px, 3.5vw, 24px); width: 100%;
  }
  .kicker {
    display: inline-block; background: var(--c); font-weight: 700; font-size: .78rem;
    text-transform: uppercase; letter-spacing: .8px; padding: 4px 12px;
    border: 2.5px solid var(--ink); border-radius: 999px; box-shadow: 2px 2px 0 var(--ink); margin-bottom: 8px;
  }
  .sec-head { text-align: center; }
  .sec-title {
    font-family: var(--f-comic); font-size: clamp(1.8rem, 5vw, 2.6rem);
    letter-spacing: 1.2px; margin: 4px 0 8px; line-height: 1.08; text-shadow: 2px 2px 0 #fff;
  }
  .sec-sub { margin: 0 auto; font-size: .95rem; color: var(--ink2); font-weight: 600; }
  .btn {
    display: inline-flex; align-items: center; justify-content: center; gap: 6px; width: 100%;
    padding: 11px 16px; font-weight: 700; font-size: .95rem; color: var(--ink);
    background: var(--y); border: var(--b); border-radius: 999px; box-shadow: 3px 3px 0 var(--ink);
    transition: transform .14s ease;
  }
  .btn:hover { transform: translate(-1px, -2px); box-shadow: 5px 5px 0 var(--ink); }
  .btn:active { transform: translate(1px, 1px); box-shadow: 2px 2px 0 var(--ink); }
  .bg-y { background: var(--y); } .bg-c { background: var(--c); } .bg-p { background: var(--p); color: #fff; }
  .bg-l { background: var(--l); } .bg-o { background: var(--o); color: #fff; } .bg-v { background: var(--v); color: #fff; }

  /* Hero */
  .pills { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 12px; }
  .tag {
    font-size: .76rem; font-weight: 700; padding: 3px 10px;
    border: 2px solid var(--ink); border-radius: 999px; box-shadow: 2px 2px 0 var(--ink);
  }
  .hero-title {
    font-family: var(--f-comic); font-size: clamp(2rem, 6vw, 3rem);
    line-height: 1.05; letter-spacing: 1.2px; margin: 0 0 12px;
  }
  .hero-title span {
    display: inline-block; background: var(--y); padding: 1px 10px;
    border: var(--b); border-radius: 12px; box-shadow: 3px 3px 0 var(--ink);
  }
  .hero-sub { font-size: .96rem; color: var(--ink2); margin: 0 0 14px; font-weight: 500; }
  .stat-row {
    display: flex; justify-content: space-between; align-items: center;
    background: var(--soft); border: 2.5px solid var(--ink); border-radius: 12px;
    padding: 8px 14px; box-shadow: 2px 2px 0 var(--ink); font-weight: 700;
  }
  .stat-num { font-family: var(--f-comic); font-size: 1.45rem; letter-spacing: 1px; }

  /* Demo Widget */
  .demo { background: linear-gradient(155deg, #33E1FF 0%, #74F2FF 52%, #FFE135 100%); }
  .demo-top { display: flex; justify-content: space-between; align-items: center; gap: 8px; flex-wrap: wrap; margin-bottom: 12px; }
  .sfx-btn { background: var(--l); border: 2.5px solid var(--ink); border-radius: 999px; padding: 4px 12px; font-weight: 700; font-size: .8rem; box-shadow: 2px 2px 0 var(--ink); }
  .sfx-btn.muted { background: #E5E7EB; }
  .stage {
    position: relative; height: 205px; background: rgba(255,253,245,.92);
    border: var(--b); border-radius: 16px; display: flex; flex-direction: column;
    align-items: center; justify-content: flex-end; padding-bottom: 14px;
    margin-bottom: 12px; overflow: hidden; user-select: none;
  }
  .hint { position: absolute; bottom: 6px; right: 10px; font-size: .72rem; font-weight: 700; opacity: .75; }
  .burst {
    position: absolute; top: 8px; left: 50%; transform: translateX(-50%) scale(.2);
    opacity: 0; pointer-events: none; z-index: 5;
  }
  .burst.show { animation: pop 1.4s cubic-bezier(.22,1.35,.36,1) forwards; }
  @keyframes pop {
    0% { opacity: 0; transform: translateX(-50%) scale(.2) rotate(-12deg); }
    18% { opacity: 1; transform: translateX(-50%) scale(1.15) rotate(4deg); }
    80% { opacity: 1; transform: translateX(-50%) scale(1) rotate(-2deg); }
    100% { opacity: 0; transform: translateX(-50%) scale(.8) translateY(-8px); }
  }
  .burst-box { position: relative; width: 184px; height: 84px; display: flex; align-items: center; justify-content: center; }
  .burst-box svg { position: absolute; inset: 0; width: 100%; height: 100%; filter: drop-shadow(3px 3px 0 #161622); }
  .burst-word {
    position: relative; z-index: 2; font-family: var(--f-comic); font-size: 1.85rem;
    letter-spacing: 1.5px; color: #fff; -webkit-text-stroke: 2px #161622; text-shadow: 2px 2px 0 #161622;
  }
  .mascot { background: transparent; border: none; padding: 0; animation: bob 2.4s ease-in-out infinite; }
  .mascot.squish { animation: squish .42s cubic-bezier(.34,1.56,.64,1); }
  @keyframes bob { 0%,100% { transform: translateY(0); } 50% { transform: translateY(-6px); } }
  @keyframes squish {
    0% { transform: scale(1); } 30% { transform: scale(1.22,.78) translateY(7px); }
    60% { transform: scale(.88,1.15) translateY(-12px); } 100% { transform: scale(1); }
  }
  .m-shadow { width: 88px; height: 14px; background: rgba(22,22,34,.2); border-radius: 50%; margin-top: -4px; }

  /* Retro LCD */
  .lcd-wrap { background: #1B241D; border: var(--b); border-radius: 14px; padding: 7px; box-shadow: 3px 3px 0 var(--ink); margin-bottom: 12px; }
  .lcd { background: #081A0C; border: 2px solid #378244; border-radius: 8px; padding: 9px 11px; font-family: var(--f-mono); }
  .lcd-h { display: flex; justify-content: space-between; font-size: .68rem; color: #39B852; border-bottom: 1px solid rgba(57,255,90,.3); padding-bottom: 4px; margin-bottom: 6px; }
  .led { display: inline-block; width: 7px; height: 7px; border-radius: 50%; background: #39FF5A; box-shadow: 0 0 6px #39FF5A; animation: blink 1s steps(2) infinite; }
  @keyframes blink { 0%,100% { opacity: 1; } 50% { opacity: .25; } }
  .lcd-txt { color: #39FF5A; font-size: .9rem; font-weight: 700; min-height: 2.5em; text-shadow: 0 0 6px rgba(57,255,90,.5); word-break: break-word; }

  /* Feature Cards (1 Column) */
  .feat { display: flex; flex-direction: column; gap: 10px; }
  .feat-top { display: flex; align-items: center; gap: 12px; }
  .ico {
    width: 48px; height: 48px; flex-shrink: 0; border-radius: 14px; border: var(--b);
    box-shadow: 3px 3px 0 var(--ink); display: flex; align-items: center; justify-content: center; font-size: 1.45rem;
  }
  .feat h3 { font-family: var(--f-comic); font-size: 1.45rem; letter-spacing: .8px; margin: 0; line-height: 1.1; }
  .feat p { margin: 0; font-size: .92rem; color: var(--ink2); }
  .chips { display: flex; flex-wrap: wrap; gap: 6px; }
  .chip { font-size: .74rem; font-weight: 700; padding: 2px 9px; border: 2px solid var(--ink); border-radius: 999px; background: var(--soft); }

  /* Explorer Tabs */
  .tabs { display: flex; flex-wrap: wrap; gap: 8px; padding-bottom: 14px; border-bottom: 3px dashed var(--ink); margin-bottom: 16px; }
  .t-btn {
    flex: 1 1 140px; padding: 9px 12px; font-weight: 700; font-size: .88rem;
    background: var(--soft); border: var(--b); border-radius: 999px; box-shadow: 2px 2px 0 var(--ink);
  }
  .t-btn.active { background: var(--p); color: #fff; box-shadow: 4px 4px 0 var(--ink); }
  .panel { display: none; } .panel.active { display: block; }
  .filters { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 12px; }
  .f-pill { padding: 5px 11px; font-weight: 700; font-size: .8rem; background: #fff; border: 2px solid var(--ink); border-radius: 999px; }
  .f-pill.active { background: var(--y); box-shadow: 2px 2px 0 var(--ink); }
  .scroll-list { max-height: 360px; overflow-y: auto; padding-right: 4px; }
  .item-row {
    background: #fff; border: 2.5px solid var(--ink); border-radius: 12px;
    padding: 10px 12px; box-shadow: 2px 2px 0 var(--ink);
  }
  .item-top { display: flex; justify-content: space-between; align-items: center; gap: 8px; margin-bottom: 3px; }
  .cat { font-size: .68rem; font-weight: 700; padding: 2px 8px; border: 2px solid var(--ink); border-radius: 999px; white-space: nowrap; }
  .cat-Basic { background: var(--c); } .cat-Interactive { background: var(--o); color: #fff; }
  .cat-Activity { background: var(--l); } .cat-Emotion { background: var(--p); color: #fff; }
  .jackpot { background: linear-gradient(135deg, #FFF3A1 0%, #FFD43B 55%, #FFAA2B 100%); border: var(--b); border-radius: 16px; padding: 14px; margin-bottom: 14px; }
  .ice-box { background: #0B192B; border: var(--b); border-radius: 16px; padding: 16px; color: #fff; }
  .ice-pill { background: #081626; border: 2px solid #5FE1FF; border-radius: 12px; padding: 12px; margin-bottom: 12px; box-shadow: 0 0 14px rgba(95,225,255,.22); }
  .ice-h { display: flex; justify-content: space-between; font-family: var(--f-mono); font-size: .7rem; color: #78E8FF; border-bottom: 1px solid rgba(95,225,255,.35); padding-bottom: 5px; margin-bottom: 8px; }
  .ice-txt { color: #B8F4FF; font-weight: 600; font-size: .94rem; min-height: 3em; }
  .mono-tag { font-family: var(--f-mono); font-size: .82rem; font-weight: 700; background: var(--y); padding: 2px 8px; border: 2px solid var(--ink); border-radius: 6px; display: inline-block; margin-bottom: 6px; }

  /* Pricing */
  .pro-card { background: linear-gradient(165deg, #FFF8CC 0%, #FFE135 55%, #FFB732 100%); position: relative; }
  .ribbon {
    display: inline-block; background: var(--p); color: #fff; font-family: var(--f-comic);
    font-size: 1.05rem; letter-spacing: 1px; padding: 4px 14px; border: var(--b);
    border-radius: 999px; box-shadow: 3px 3px 0 var(--ink); margin-bottom: 8px;
  }
  .plist { list-style: none; padding: 0; margin: 12px 0 16px; display: flex; flex-direction: column; gap: 9px; }
  .plist li { display: flex; align-items: flex-start; gap: 9px; font-size: .92rem; }
  .chk {
    width: 22px; height: 22px; flex-shrink: 0; border-radius: 50%; border: 2px solid var(--ink);
    background: var(--l); display: inline-flex; align-items: center; justify-content: center; font-weight: 700; font-size: .78rem;
  }

  /* Footer */
  .footer { background: var(--ink); color: var(--cream); border: var(--b); border-radius: 18px; padding: 18px; text-align: center; }
  .footer-brand { font-family: var(--f-comic); font-size: 1.6rem; color: var(--y); letter-spacing: 1.2px; margin-bottom: 4px; }
  .footer p { margin: 0 0 10px; font-size: .85rem; color: #D1D5DB; }
  .f-chips { display: flex; flex-wrap: wrap; justify-content: center; gap: 6px; }
  .f-chip { background: #252538; color: var(--c); border: 1.5px solid var(--c); border-radius: 999px; padding: 3px 10px; font-size: .75rem; font-weight: 700; }
</style>
</head>
<body>
<div class="wrap" id="top">

  <!-- 1. HEADER -->
  <header class="topbar">
    <a href="#top" class="logo"><span class="dot"></span>AATCHI!</a>
    <nav class="nav" aria-label="Navigation">
      <a href="#features">Features</a>
      <a href="#explorer" data-jump="actions">Actions &amp; Hijinks</a>
      <a href="#explorer" data-jump="ai">AI Brain</a>
      <a href="#explorer" data-jump="stack">Tech Stack</a>
      <a href="#pricing" class="pro-link">Free vs Pro</a>
    </nav>
  </header>

  <!-- 2. HERO (1 COLUMN) -->
  <section class="card col">
    <div class="pills">
      <span class="tag bg-c">AATCHI.exe • Windows Native</span>
      <span class="tag bg-l">100% .avatar ZIP Compatible</span>
      <span class="tag bg-y">C++20 + OpenGL 3.3</span>
    </div>
    <h1 class="hero-title"><span>AATCHI</span> — Your Living Cartoon Desktop Buddy!</h1>
    <p class="hero-sub">
      A standalone interactive Windows desktop companion &amp; <strong>.avatar</strong> player built in native
      <strong>C++20, SDL3, OpenGL 3.3, Dear ImGui, FFmpeg, and Win32 API</strong>.
      100% compatible with <em>Dance Avatar Studio</em> — packed with desktop physics, 60 comic bursts, 240+ LCD quips, and an optional kid-safe AI brain!
    </p>
    <div class="col" style="gap:10px;">
      <a href="#explorer" class="btn bg-p">Explore 38+ Actions &amp; 26 Hijinks</a>
      <a href="#pricing" class="btn bg-c">Free vs. Pro ($0.99)</a>
    </div>
    <div class="col" style="gap:8px;margin-top:4px;">
      <div class="stat-row"><span>Animated Actions</span><span class="stat-num">38+</span></div>
      <div class="stat-row"><span>Random Desktop Hijinks</span><span class="stat-num">26</span></div>
      <div class="stat-row"><span>Retro Comic Bursts</span><span class="stat-num">60</span></div>
      <div class="stat-row"><span>Green LCD Quips</span><span class="stat-num">240+</span></div>
    </div>
  </section>

  <!-- 3. INTERACTIVE CARTOON DEMO (1 COLUMN) -->
  <section class="card demo">
    <div class="demo-top">
      <span class="tag" style="background:var(--cream);">Interactive Desktop Preview</span>
      <button type="button" class="sfx-btn" id="sfxBtn">SFX: ON 🔊</button>
    </div>

    <div class="stage">
      <div class="burst" id="burst" aria-live="polite">
        <div class="burst-box">
          <svg viewBox="0 0 220 110" aria-hidden="true">
            <polygon id="bOut" fill="#FF2818" stroke="#161622" stroke-width="4" points="110,4 128,24 156,8 160,32 194,22 184,48 214,56 184,68 198,92 164,84 158,106 130,88 110,106 90,88 62,106 56,84 22,92 36,68 6,56 36,48 26,22 60,32 64,8 92,24" />
            <polygon id="bIn" fill="#FFE818" stroke="#161622" stroke-width="3" points="110,14 124,30 148,18 152,38 180,32 172,52 196,58 172,66 182,84 156,78 150,95 126,80 110,95 94,80 70,95 64,78 38,84 48,66 24,58 48,52 40,32 68,38 72,18 96,30" />
          </svg>
          <span class="burst-word" id="bWord">POW!</span>
        </div>
      </div>

      <button type="button" class="mascot" id="mascot" aria-label="Click AATCHI mascot">
        <svg width="124" height="124" viewBox="0 0 140 140" aria-hidden="true">
          <polygon points="28,52 22,14 58,36" fill="#FFF2F8" stroke="#161622" stroke-width="5" stroke-linejoin="round" />
          <polygon points="32,45 29,24 50,37" fill="#FF7AA8" />
          <polygon points="112,52 118,14 82,36" fill="#FFF2F8" stroke="#161622" stroke-width="5" stroke-linejoin="round" />
          <polygon points="108,45 111,24 90,37" fill="#FF7AA8" />
          <ellipse cx="70" cy="80" rx="50" ry="46" fill="#FFF7FB" stroke="#161622" stroke-width="5" />
          <ellipse cx="70" cy="94" rx="30" ry="20" fill="#FFE6F2" />
          <circle cx="51" cy="74" r="8.5" fill="#161622" /><circle cx="89" cy="74" r="8.5" fill="#161622" />
          <circle cx="48" cy="70.5" r="3" fill="#fff" /><circle cx="86" cy="70.5" r="3" fill="#fff" />
          <ellipse cx="36" cy="85" rx="8.5" ry="5" fill="#FF7AA8" opacity=".85" />
          <ellipse cx="104" cy="85" rx="8.5" ry="5" fill="#FF7AA8" opacity=".85" />
          <path d="M58 86 Q64 93 70 86 Q76 93 82 86" fill="none" stroke="#161622" stroke-width="4" stroke-linecap="round" />
          <circle cx="22" cy="88" r="9" fill="#FFF2F8" stroke="#161622" stroke-width="4" />
          <circle cx="118" cy="88" r="9" fill="#FFF2F8" stroke="#161622" stroke-width="4" />
        </svg>
      </button>
      <div class="m-shadow"></div>
      <span class="hint">Click AATCHI! 👆</span>
    </div>

    <div class="lcd-wrap">
      <div class="lcd">
        <div class="lcd-h">
          <span><span class="led"></span> LCD // 14400</span>
          <span>RETRO QUIP BAR</span>
        </div>
        <div class="lcd-txt"><span id="lcdOut">Boss incoming!</span><span style="animation:blink .7s steps(2) infinite;">_</span></div>
      </div>
    </div>

    <div class="col" style="gap:8px;">
      <button type="button" class="btn bg-y" id="popBtn">💥 Pop Comic Word</button>
      <button type="button" class="btn bg-l" id="quipBtn">📟 Next LCD Quip</button>
    </div>
  </section>

  <!-- 4. FEATURES (STRICTLY 1 COLUMN) -->
  <section id="features" class="col">
    <div class="sec-head">
      <span class="kicker">Packed With Desktop Magic</span>
      <h2 class="sec-title">6 Superpowers Built Into AATCHI.exe</h2>
      <p class="sec-sub">Native Windows C++20 engine designed to make your monitor feel alive without slowing down your PC.</p>
    </div>

    <article class="card feat">
      <div class="feat-top"><div class="ico bg-y">🧱</div><h3>Desktop Physics &amp; Collisions</h3></div>
      <p>Real-time open window platforming &amp; visible desktop icon detection via UI Automation! Sits on your Recycle Bin, bonks into apps, performs <strong>4-way cartoon gravity falls</strong> with bouncy rebounds, and roams across multi-monitor setups.</p>
      <div class="chips"><span class="chip">Window Platforming</span><span class="chip">4-Way Gravity</span><span class="chip">Multi-Monitor</span></div>
    </article>

    <article class="card feat">
      <div class="feat-top"><div class="ico bg-p">✨</div><h3>5 GPU Render FX &amp; 13 Anime Backdrops</h3></div>
      <p>Right-click to fire GPU shaders: <strong>Strobe Flash, Rainbow Color, Neon RGB Glitch, Golden Aura,</strong> and <strong>Hologram Shimmer</strong> — plus 13 dramatic 10-second anime FX like Matrix Rain, Mech HUD, Synthwave, Black Hole Warp, and Flame Aura.</p>
      <div class="chips"><span class="chip">OpenGL 3.3 Shaders</span><span class="chip">13 Anime FX</span><span class="chip">Right-Click Magic</span></div>
    </article>

    <article class="card feat">
      <div class="feat-top"><div class="ico bg-c">🧠</div><h3>Smart PC Context Awareness</h3></div>
      <p>Reacts to <strong>10 Windows hotkeys</strong> (Ctrl+C/V/Z/S/X/A/F, Alt+Tab, Alt+F4, Ctrl+Alt+Del), dances to music via the <strong>WASAPI audio peak meter</strong>, alerts on battery/charging, pops hourly clock &amp; date banners, and follows a daily routine.</p>
      <div class="chips"><span class="chip">10 Hotkeys</span><span class="chip">WASAPI Beat Dance</span><span class="chip">Battery &amp; Clock</span></div>
    </article>

    <article class="card feat">
      <div class="feat-top"><div class="ico bg-o">🔊</div><h3>Retro Audio Synth &amp; Live Typing</h3></div>
      <p>Zero sound bloat: <strong>36 procedural cartoon &amp; arcade SFX</strong> (Slide Whistle, Rubber Boing, 1966 Batman Brass Hit, 8-Bit Coin, Typewriter Clack), <strong>75 funny SAPI voice lines</strong>, and an ephemeral sunset-gradient live typing ticker.</p>
      <div class="chips"><span class="chip">36 Synth SFX</span><span class="chip">75 SAPI Voices</span><span class="chip">Sunset Ticker</span></div>
    </article>

    <article class="card feat">
      <div class="feat-top"><div class="ico bg-l">💥</div><h3>60 Comic Bursts &amp; 240+ LCD Quips</h3></div>
      <p>Classic jagged starburst pop-ups (<em>POW!, BOING!, KAPOW!, YEET!, BWAHAHA!</em>) paired with a glowing phosphor-green <code>LCD // 14400</code> ticker packed with 240+ work, gaming, hacker, and desktop quips.</p>
      <div class="chips"><span class="chip">60 Starbursts</span><span class="chip">240+ Quips</span><span class="chip">Vertical Stack</span></div>
    </article>

    <article class="card feat">
      <div class="feat-top"><div class="ico bg-v">🛡️</div><h3>Kid-Safe &amp; Lightweight Native C++</h3></div>
      <p>Transparent frameless Win32 DWM window, smart click-through headroom, clean tray menu, zero spyware, ephemeral typing (never saved), and strict kid-safe AI guardrails.</p>
      <div class="chips"><span class="chip">Click-Through</span><span class="chip">Zero Spyware</span><span class="chip">Kid-Safe AI</span></div>
    </article>
  </section>

  <!-- 5. INTERACTIVE EXPLORER (1 COLUMN) -->
  <section id="explorer" class="card">
    <div class="sec-head" style="margin-bottom:14px;">
      <span class="kicker">Interactive Encyclopedia</span>
      <h2 class="sec-title">Explore Everything Inside AATCHI!</h2>
    </div>

    <div class="tabs" role="tablist">
      <button type="button" class="t-btn active" data-tab="actions">🎬 38+ Actions</button>
      <button type="button" class="t-btn" data-tab="hijinks">🎪 26 Hijinks</button>
      <button type="button" class="t-btn" data-tab="ai">🤖 AI Engine</button>
      <button type="button" class="t-btn" data-tab="stack">⚙️ Tech Stack</button>
    </div>

    <!-- Tab 1: Actions -->
    <div class="panel active" id="p-actions">
      <div class="filters" id="filters">
        <button type="button" class="f-pill active" data-cat="All">All (38)</button>
        <button type="button" class="f-pill" data-cat="Basic">Basic (14)</button>
        <button type="button" class="f-pill" data-cat="Interactive">Interactive (7)</button>
        <button type="button" class="f-pill" data-cat="Activity">Activity (7)</button>
        <button type="button" class="f-pill" data-cat="Emotion">Emotion (10)</button>
      </div>
      <div class="col scroll-list" id="actionsList"></div>
    </div>

    <!-- Tab 2: Hijinks -->
    <div class="panel" id="p-hijinks">
      <div class="jackpot col">
        <strong style="font-family:var(--f-comic);font-size:1.45rem;letter-spacing:1px;">🌟 RARE 12% JACKPOT EVENTS!</strong>
        <div class="item-row"><strong>🛸 UFO Abduction Beam</strong><p style="margin:3px 0 0;font-size:.84rem;">A saucer beams AATCHI halfway up with a green tractor beam — then drops him with "NOPE!"</p></div>
        <div class="item-row"><strong>🥷 Ninja Smoke Bomb</strong><p style="margin:3px 0 0;font-size:.84rem;">Vanishes in a cartoon smoke cloud and teleports instantly across your screen!</p></div>
        <div class="item-row"><strong>⚡ Super Power-Up Aura</strong><p style="margin:3px 0 0;font-size:.84rem;">4 seconds of intense golden energy rings &amp; sparks — then immediately gets tired.</p></div>
      </div>
      <div class="col scroll-list" id="hijinksList"></div>
    </div>

    <!-- Tab 3: AI Engine -->
    <div class="panel col" id="p-ai">
      <div>
        <span class="kicker bg-l">ai.h &amp; ai.cpp • Non-Blocking WinHTTP</span>
        <h3 style="font-family:var(--f-comic);font-size:1.7rem;margin:4px 0 8px;">Multi-Provider AI Brain With Zero UI Freeze</h3>
        <p style="margin:0 0 10px;font-size:.92rem;color:var(--ink2);">
          Type any question and press <strong>Enter</strong> (or get a random tip every 10–15 min). <code>AiChatEngine</code> runs native <strong>WinHTTP HTTPS</strong> on a background worker thread.
        </p>
        <div class="col" style="gap:8px;margin-bottom:10px;">
          <div class="item-row"><strong>Groq / xAI Grok</strong> — <code>api.groq.com / api.x.ai</code></div>
          <div class="item-row"><strong>Google Gemini</strong> — <code>v1beta generateContent</code></div>
          <div class="item-row"><strong>OpenAI ChatGPT</strong> — <code>api.openai.com/v1</code></div>
        </div>
        <ul style="padding-left:18px;margin:0;font-size:.9rem;">
          <li><strong>BYO Keys &amp; Failover:</strong> Round-robin rotation with automatic error fallback.</li>
          <li><strong>Self-Healing <code>/models</code>:</strong> Auto-fetches live models asynchronously.</li>
          <li><strong>Kid-Safe Guardrails:</strong> Strips <code>&lt;think&gt;</code> tags &amp; caps replies at 180 clean chars.</li>
        </ul>
      </div>

      <div class="ice-box">
        <div class="ice-pill">
          <div class="ice-h"><span id="aiProv">AI // PROMPT ROLLER</span><span>20s FROST PILL</span></div>
          <div class="ice-txt" id="aiTxt">Click below to preview one of the built-in desktop prompts from ai.cpp!</div>
        </div>
        <button type="button" class="btn bg-c" id="rollAi">🎲 Roll Random PC Question</button>
        <p id="aiMeta" style="margin:8px 0 0;font-size:.78rem;color:#9DD8EE;">Loaded from <code>kDesktopUserQuestions[100]</code> in <code>ai.cpp</code>.</p>
      </div>
    </div>

    <!-- Tab 4: Source & Stack -->
    <div class="panel col" id="p-stack">
      <div class="chips">
        <span class="chip bg-y">C++20</span><span class="chip bg-c">SDL3</span><span class="chip bg-p" style="color:#fff;">OpenGL 3.3</span>
        <span class="chip bg-l">Dear ImGui</span><span class="chip bg-o" style="color:#fff;">FFmpeg</span><span class="chip bg-v" style="color:#fff;">miniz</span>
        <span class="chip bg-y">WinHTTP</span><span class="chip bg-c">Win32 / DWM</span><span class="chip bg-l">WASAPI</span>
        <span class="chip bg-p" style="color:#fff;">UI Automation</span><span class="chip bg-o" style="color:#fff;">SAPI TTS</span>
      </div>
      <div class="col">
        <div class="item-row"><span class="mono-tag">avatar_desktop_main.cpp</span><p style="margin:0;font-size:.86rem;">Entry point (<code>AATCHI.exe</code>), SDL3+OpenGL transparent DWM window, 36-sound <code>SynthAudioPlayer</code>, tray &amp; ImGui menu, <code>SafeDesktopObstacleScanner</code>, <code>Win32ContextMonitor</code>.</p></div>
        <div class="item-row"><span class="mono-tag">companion_engine.h</span><p style="margin:0;font-size:.86rem;">Defines <code>AnimState</code>, 36 <code>RetroSfxId</code>, 26 <code>SpecialHijinkKind</code>, 13 <code>BgAnimeKind</code>, 5 GPU <code>RenderFxKind</code>, and <code>CompanionEngine</code>.</p></div>
        <div class="item-row"><span class="mono-tag">companion_engine.cpp</span><p style="margin:0;font-size:.86rem;">State machine, 38 actions, shuffle bag, 60 comic bursts, 240+ LCD quips, 75 SAPI voices, 4-way gravity &amp; collisions, GPU FX.</p></div>
        <div class="item-row"><span class="mono-tag">ai.h</span><p style="margin:0;font-size:.86rem;">Thread-safe interface for <code>AiChatEngine</code>: non-blocking <code>askAsync()</code>, <code>popReply()</code>, and <code>refreshModelsAsync()</code>.</p></div>
        <div class="item-row"><span class="mono-tag">ai.cpp</span><p style="margin:0;font-size:.86rem;">WinHTTP HTTPS client for Groq, xAI Grok, Gemini, ChatGPT, kid-safe system prompt, 100 desktop questions, 180-char finalizer.</p></div>
      </div>
    </div>
  </section>

  <!-- 6. FREE VS PRO (1 COLUMN) -->
  <section id="pricing" class="col">
    <div class="sec-head">
      <span class="kicker bg-o" style="color:#fff;">No Subscriptions • No Ads</span>
      <h2 class="sec-title">Free Edition vs. AATCHI PRO ($0.99!)</h2>
      <p class="sec-sub">Start free on your desktop, or unlock unlimited avatars, 4 bonus addons, and AATCHI-Editor Studio forever.</p>
    </div>

    <div class="card">
      <h3 style="font-family:var(--f-comic);font-size:1.8rem;margin:0 0 4px;">FREE EDITION</h3>
      <p style="margin:0;font-weight:700;color:var(--ink2);">$0 Forever • Starter Desktop Companion</p>
      <ul class="plist">
        <li><span class="chk" style="background:var(--c);">✓</span><span>Up to <strong>3 bundled avatars</strong> (<code>AATCHI.avatar</code>, <code>liberty.avatar</code>, <code>Yo.avatar</code>)</span></li>
        <li><span class="chk">✓</span><span>Full transparent Win32 window, click-through mode, 60 bursts, 240+ quips &amp; 26 hijinks</span></li>
        <li><span class="chk">✓</span><span>Window platforming, icon collisions, 4-way gravity, 36 SFX, 75 voices &amp; BYO-key AI chat</span></li>
      </ul>
      <a href="#top" class="btn bg-c">Try the Interactive Demo Above ☝️</a>
    </div>

    <div class="card pro-card">
      <span class="ribbon">ONLY $0.99 ONE-TIME!</span>
      <h3 style="font-family:var(--f-comic);font-size:1.85rem;margin:0 0 4px;">AATCHI PRO EDITION</h3>
      <p style="margin:0 0 10px;font-weight:700;color:var(--ink2);">$0.99 One-Time on Microsoft Store • Own Forever</p>
      <div class="chips" style="margin-bottom:8px;">
        <span class="chip" style="background:#FFD1E8;">🌟 Addon #1</span>
        <span class="chip" style="background:#C8F4FF;">🎁 Addon #2</span>
        <span class="chip" style="background:#FFE8A3;">⚡ Addon #3</span>
        <span class="chip" style="background:#C8FFD6;">👑 Addon #4</span>
      </div>
      <ul class="plist">
        <li><span class="chk">✓</span><span><strong>UNLIMITED Avatars:</strong> Drag-and-drop 10, 50, or 500+ community <code>.avatar</code> packs!</span></li>
        <li><span class="chk">✓</span><span><strong>4 Bonus Character Addons</strong> &amp; Auto-Rotation (every 4 hours or daily)</span></li>
        <li><span class="chk">✓</span><span><strong>AATCHI-Editor Studio:</strong> Import <code>.WebM</code>, <code>.WebP</code>, <code>.MP4</code> with Chroma/Luma Key, Cropper, Trimmer &amp; 1-Click <code>.avatar</code> ZIP export!</span></li>
      </ul>
      <button type="button" class="btn bg-p" id="proBtn">🚀 Unlock Everything Forever — $0.99 MS Store</button>
    </div>
  </section>

  <!-- 7. FOOTER -->
  <footer class="footer">
    <div class="footer-brand">AATCHI! Desktop Companion</div>
    <p>Built with native C++20, SDL3, OpenGL 3.3, Dear ImGui, FFmpeg, miniz, and Win32 API. 100% Dance Avatar Studio compatible.</p>
    <div class="f-chips">
      <span class="f-chip">AATCHI.exe</span><span class="f-chip">Windows Native</span><span class="f-chip">Kid-Safe</span><span class="f-chip">Zero Spyware</span>
    </div>
  </footer>

</div>

<script>
(() => {
  const BURSTS = [
    ['POW!','#FFE818','#F02818'],['BOING!','#50F035','#209010'],['KAPOW!','#FFD815','#E02010'],
    ['BANG!','#FF5520','#FFE010'],['NYOOM!','#FFFF20','#6025FF'],['ZAP!','#25E8FF','#1545FF'],
    ['YEET!','#FFF035','#5525FF'],['LEVEL UP!','#FFF525','#FF9015'],['TA-DA!','#FFF025','#9035FF'],
    ['WHOA!','#30E5FF','#2045FF'],['BEEP! BEEP!','#FFF025','#FF5510'],['BWAHAHA!','#65F545','#C01585']
  ];
  const QUIPS = [
    'Boss incoming!','74 tabs open. Bold choice.','Downloading more RAM...','I ate your autosave.',
    'Rent-free on your screen.','404: Motivation not found.','Parkour! Desktop parkour!','Quick! Open Excel!',
    'Your fans sound like a jet.','Posture check! Sit up!','CONNECT 14400','Gravity? Optional today.',
    'Sitting on Recycle Bin!','Whoa! Almost hit an icon!'
  ];
  const ACTIONS = [
    ['Idle','Basic','Natural breathing, blinking, and small movements.'],
    ['Hello','Basic','Wave playfully at the user.'],
    ['Sleep','Basic','Close eyes and sleep with floating Z symbols.'],
    ['Wait','Basic','Stand and look around patiently.'],
    ['Dance','Basic','Perform a cute energetic dance.'],
    ['Funny Move','Basic','Perform a random silly movement.'],
    ['Walk Left','Basic','Walk across the desktop toward the left.'],
    ['Walk Right','Basic','Walk across the desktop toward the right.'],
    ['Walk Up','Basic','Walk or move upwards on the desktop screen.'],
    ['Walk Down','Basic','Walk or move downwards on the desktop screen.'],
    ['Walk Random','Basic','Roam freely in random directions across the screen.'],
    ['Angry','Basic','Angry face, stomping, and frustration.'],
    ['No','Basic','Shake head to refuse or disagree.'],
    ['Yes','Basic','Nod head enthusiastically in agreement.'],
    ['Peek','Interactive','Hide behind screen edges or windows and slowly peek out.'],
    ['Window Climb','Interactive','Climb the side of an active window and sit on its title bar.'],
    ['Cursor Chase','Interactive','Run after the mouse pointer or playfully swat at it.'],
    ['Drag Dangle','Interactive','Flail legs and look surprised when dragged across the screen.'],
    ['Falling','Interactive','Fall with flailing arms and bounce upon landing.'],
    ['Screen Knock','Interactive','Walk to the front of the screen and knock on the glass.'],
    ['Trip & Fall','Interactive','Stumble over nothing while walking, faceplant, and get back up.'],
    ['Eating','Activity','Pull out ramen, rice balls, or a cookie and munch on it.'],
    ['Typing','Activity','Sit down with a tiny laptop or console and tap away.'],
    ['Reading','Activity','Open a tiny book or manga and flip through pages.'],
    ['Music','Activity','Put on headphones and bob head to a beat.'],
    ['Stretching','Activity','Reach arms up high and yawn after sitting idle.'],
    ['Sitting','Activity','Sit down comfortably and relax on the desktop.'],
    ['Drinking','Activity','Take a refreshing sip from a tiny cup or mug.'],
    ['Shocked','Emotion','Wide eyes, open mouth, lightning bolts or sweat drops.'],
    ['Shy / Blushing','Emotion','Turn red, hide face in hands, and fidget nervously.'],
    ['Sparkling Eyes','Emotion','Huge starry eyes when excited or hovered over.'],
    ['Crying','Emotion','Sit on the ground with exaggerated cartoon waterfall tears.'],
    ['Power Up','Emotion','Clench fists while a glowing shonen aura flares up.'],
    ['Smug Grin','Emotion','Cross arms and give a cheeky, confident smirk.'],
    ['Dizzy','Emotion','Small stars spin around head after shaking or dropping.'],
    ['Happy','Emotion','Smile brightly and bounce with joy.'],
    ['Curious','Emotion','Tilt head and investigate with interest.'],
    ['Bored','Emotion','Look around slowly and sigh.']
  ];
  const HIJINKS = [
    ['✨ Fade Teleport','Splits into clone ghosts and warps to a brand-new spot.'],
    ['🪟 Titlebar Warp','Teleports right on top of your foreground window titlebar.'],
    ['👀 4-Corner Peek','Ambushes you by peeking from one of the 4 screen corners.'],
    ['🔍 Close-Up Jump','Zooms 2.2x up to the monitor glass and knocks!'],
    ['⭐ Toy Chase','Spawns a bouncing Golden Star, Beach Ball, or Ramen Bowl.'],
    ['🎱 Pinball Bounce','Ricochets diagonally off all four screen edges!'],
    ['🙃 Ceiling Hang','Hangs from the top monitor edge, then drops and rebounds.'],
    ['💥 Earthquake Slam','Leaps high and slams the taskbar with screen shake!'],
    ['🌀 360° Spin Flip','Pulls off an acrobatic mid-air spin with a springy landing.'],
    ['👻 Ghost Sneak','Fades to 15% opacity ("SNEAKY!"), then pops "BOO!"'],
    ['🎤 Stage Spotlight','Drops a glowing stage beam and musical notes for a concert.'],
    ['✈️ Airplane Toss','Tosses a gliding paper airplane or star and sprints after it.'],
    ['🎈 Balloon Float','Floats upward holding a balloon until it POPs at the top!'],
    ['☔ Rain Cloud','Tiny cartoon cloud follows overhead while popping an umbrella.'],
    ['🎣 Window Fishing','Perches on your window edge and reels up a boot, fish, or star.'],
    ['💻 Gaming Session','Pulls out a mini laptop, mashes keys, then hits GG! or Rage Quit.'],
    ['🍕 Snack Break','Enjoys a steaming mug, pizza slice, or donut for energy.'],
    ['🤧 Sneeze Blast','Builds up "ah... ah... AATCHI!" and blasts backward!'],
    ['💨 Ninja Run','Sprints with anime speed lines and poofs to the other side.'],
    ['🔵 Energy Blast','Charges an aura, fires a mini energy beam, and gets dizzy!'],
    ['⚔️ Katana Slash','Lightning-fast anime diagonal sword slash with a crisp SHING!'],
    ['💫 Clumsy Trip','Trips mid-walk ("WHOOPS!"), hops up: "...nobody saw!"'],
    ['🌈 Sparkle Spin','Rainbow-tinted transformation spin with orbiting stars.']
  ];
  const AI_Q = [
    'What is one underrated Windows keyboard shortcut everyone should know?',
    'Give a 1-sentence tip for organizing a messy Windows desktop.',
    'Share one simple way to reduce eye strain from bright monitors.',
    'Remind the user in a cute way to blink and rest their eyes for 20 seconds.',
    'Ask if the user has had a sip of water recently in a playful tone.',
    'Explain what RAM actually does using a fun everyday analogy.',
    'Why do USB plugs always seem to take three tries to plug in?',
    'Invent a funny desktop achievement the user unlocked for sitting at their PC.',
    'Pretend you are a tiny RPG NPC living on the taskbar.',
    'Give a playful boss battle pep talk for whatever task is on screen.',
    'Pretend the Recycle Bin is a treasure chest and say something funny.',
    'Explain what a firewall does using a castle-gate analogy in one line.'
  ];

  let sfxOn = true, ctx = null, lastB = -1, qIdx = 0, tmr = null;
  const $ = (id) => document.getElementById(id);

  function tone(kind) {
    if (!sfxOn) return;
    try {
      ctx = ctx || new (window.AudioContext || window.webkitAudioContext)();
      if (ctx.state === 'suspended') ctx.resume();
      const t = ctx.currentTime, o = ctx.createOscillator(), g = ctx.createGain();
      o.connect(g); g.connect(ctx.destination);
      o.type = kind === 'boing' ? 'sine' : 'triangle';
      o.frequency.setValueAtTime(kind === 'boing' ? 260 : 540, t);
      o.frequency.exponentialRampToValueAtTime(kind === 'boing' ? 620 : 810, t + .12);
      g.gain.setValueAtTime(.12, t); g.gain.exponentialRampToValueAtTime(.001, t + .22);
      o.start(t); o.stop(t + .23);
    } catch {}
  }

  function popBurst() {
    let i = Math.floor(Math.random() * BURSTS.length);
    if (i === lastB) i = (i + 1) % BURSTS.length;
    lastB = i;
    const [w, inner, outer] = BURSTS[i];
    $('bWord').textContent = w;
    $('bIn').setAttribute('fill', inner);
    $('bOut').setAttribute('fill', outer);
    $('burst').classList.remove('show'); void $('burst').offsetWidth; $('burst').classList.add('show');
    $('mascot').classList.remove('squish'); void $('mascot').offsetWidth; $('mascot').classList.add('squish');
    tone('boing');
  }

  function typeQuip(txt) {
    clearInterval(tmr); $('lcdOut').textContent = '';
    let i = 0;
    tmr = setInterval(() => {
      $('lcdOut').textContent = txt.slice(0, ++i);
      if (i >= txt.length) clearInterval(tmr);
    }, 24);
  }

  $('mascot').onclick = () => { popBurst(); if (Math.random() < .5) typeQuip(QUIPS[qIdx = (qIdx + 1) % QUIPS.length]); };
  $('popBtn').onclick = popBurst;
  $('quipBtn').onclick = () => { typeQuip(QUIPS[qIdx = (qIdx + 1) % QUIPS.length]); tone('quip'); };
  $('sfxBtn').onclick = () => {
    sfxOn = !sfxOn;
    $('sfxBtn').textContent = sfxOn ? 'SFX: ON 🔊' : 'SFX: OFF 🔇';
    $('sfxBtn').classList.toggle('muted', !sfxOn);
    if (sfxOn) tone('quip');
  };
  setInterval(() => typeQuip(QUIPS[qIdx = (qIdx + 1) % QUIPS.length]), 7500);

  function setTab(key) {
    document.querySelectorAll('.t-btn').forEach(b => b.classList.toggle('active', b.dataset.tab === key));
    document.querySelectorAll('.panel').forEach(p => p.classList.toggle('active', p.id === 'p-' + key));
  }
  document.querySelectorAll('.t-btn').forEach(b => b.onclick = () => { setTab(b.dataset.tab); tone('quip'); });
  document.querySelectorAll('[data-jump]').forEach(a => a.onclick = () => setTab(a.dataset.jump));

  function drawActions(cat) {
    const list = cat === 'All' ? ACTIONS : ACTIONS.filter(x => x[1] === cat);
    $('actionsList').innerHTML = list.map(([n, c, d]) =>
      `<div class="item-row"><div class="item-top"><strong>${n}</strong><span class="cat cat-${c}">${c}</span></div><p style="margin:0;font-size:.82rem;color:var(--ink2);">${d}</p></div>`
    ).join('');
  }
  document.querySelectorAll('.f-pill').forEach(p => p.onclick = () => {
    document.querySelectorAll('.f-pill').forEach(x => x.classList.remove('active'));
    p.classList.add('active'); drawActions(p.dataset.cat); tone('quip');
  });
  drawActions('All');

  $('hijinksList').innerHTML = HIJINKS.map(([n, d]) =>
    `<div class="item-row"><strong>${n}</strong><p style="margin:3px 0 0;font-size:.82rem;color:var(--ink2);">${d}</p></div>`
  ).join('');

  const provs = ['Groq', 'Gemini', 'ChatGPT', 'Grok'];
  let lastAi = -1;
  $('rollAi').onclick = () => {
    let i = Math.floor(Math.random() * AI_Q.length);
    if (i === lastAi) i = (i + 1) % AI_Q.length;
    lastAi = i;
    $('aiProv').textContent = 'AI // ' + provs[Math.floor(Math.random() * provs.length)].toUpperCase() + ' READY';
    $('aiTxt').textContent = '"' + AI_Q[i] + '"';
    $('aiMeta').innerHTML = `Sample prompt #${i + 1} from <code>kDesktopUserQuestions[100]</code> • Kid-safe max 180-char reply.`;
    tone('quip');
  };

  $('proBtn').onclick = () => {
    tone('boing');
    $('proBtn').textContent = '🎉 Open AATCHI Tray Menu → Upgrade ($0.99 MS Store)!';
    setTimeout(() => $('proBtn').textContent = '🚀 Unlock Everything Forever — $0.99 MS Store', 3200);
  };
})();
</script>
</body>
</html>
