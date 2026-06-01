<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>João Simões — GitHub Profile Preview</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;500;600;700;800&family=Rajdhani:wght@300;400;500;600;700&family=Bebas+Neue&display=swap');

  :root {
    --red: #E8001C;
    --red-dim: #9B0013;
    --bg: #080808;
    --bg2: #0D0D0D;
    --bg3: #111111;
    --bg4: #161616;
    --white: #FFFFFF;
    --grey: #888888;
    --grey-light: #AAAAAA;
    --border: #1E1E1E;
    --border-red: rgba(232, 0, 28, 0.3);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--white);
    font-family: 'JetBrains Mono', monospace;
    overflow-x: hidden;
    cursor: crosshair;
  }

  /* ─── SCANLINE OVERLAY ─── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.08) 2px,
      rgba(0,0,0,0.08) 4px
    );
    pointer-events: none;
    z-index: 9999;
  }

  /* ─── HERO HEADER ─── */
  .hero {
    position: relative;
    width: 100%;
    height: 320px;
    background: linear-gradient(135deg, #080808 0%, #0D0D0D 40%, #120004 70%, #080808 100%);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    border-bottom: 1px solid var(--border-red);
  }

  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background: 
      radial-gradient(ellipse 80% 50% at 50% 50%, rgba(232,0,28,0.08) 0%, transparent 70%),
      repeating-linear-gradient(90deg, transparent, transparent 80px, rgba(232,0,28,0.03) 80px, rgba(232,0,28,0.03) 81px);
  }

  .hero-stripe {
    position: absolute;
    left: 0; right: 0;
    height: 3px;
    background: linear-gradient(90deg, transparent, var(--red), transparent);
    animation: stripeMove 3s ease-in-out infinite alternate;
  }
  .hero-stripe:nth-child(1) { top: 25%; }
  .hero-stripe:nth-child(2) { bottom: 25%; opacity: 0.4; }

  @keyframes stripeMove {
    from { opacity: 0.3; transform: scaleX(0.8); }
    to { opacity: 1; transform: scaleX(1); }
  }

  .hero-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(56px, 9vw, 96px);
    letter-spacing: 0.12em;
    color: var(--white);
    position: relative;
    z-index: 2;
    text-shadow: 0 0 60px rgba(232,0,28,0.4), 0 2px 4px rgba(0,0,0,0.8);
    animation: fadeInUp 1s ease both;
  }

  .hero-name span { color: var(--red); }

  .hero-sub {
    font-family: 'Rajdhani', sans-serif;
    font-size: 13px;
    font-weight: 500;
    letter-spacing: 0.35em;
    color: var(--grey);
    text-transform: uppercase;
    position: relative;
    z-index: 2;
    margin-top: 12px;
    animation: fadeInUp 1s ease 0.2s both;
  }

  .hero-badge {
    display: flex;
    gap: 8px;
    margin-top: 20px;
    position: relative;
    z-index: 2;
    animation: fadeInUp 1s ease 0.4s both;
  }

  .hero-pill {
    background: rgba(232,0,28,0.12);
    border: 1px solid rgba(232,0,28,0.3);
    color: var(--grey-light);
    font-size: 10px;
    letter-spacing: 0.2em;
    padding: 4px 12px;
    font-family: 'Rajdhani', sans-serif;
    font-weight: 600;
  }

  /* ─── TELEMETRY BAR ─── */
  .telemetry-bar {
    background: var(--bg2);
    border-bottom: 1px solid var(--border);
    padding: 10px 0;
    overflow: hidden;
    position: relative;
  }

  .telemetry-ticker {
    display: flex;
    gap: 60px;
    white-space: nowrap;
    animation: ticker 20s linear infinite;
    font-size: 11px;
    letter-spacing: 0.15em;
    color: var(--grey);
  }

  .telemetry-ticker span { color: var(--red); }

  @keyframes ticker {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
  }

  /* ─── TYPING DISPLAY ─── */
  .typing-display {
    background: var(--bg2);
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    padding: 20px 0;
    text-align: center;
  }

  .typing-line {
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    color: var(--red);
    font-weight: 600;
    letter-spacing: 0.05em;
    opacity: 0;
    animation: typeFade 4s ease infinite;
  }

  @keyframes typeFade {
    0%, 5% { opacity: 0; }
    15%, 80% { opacity: 1; }
    95%, 100% { opacity: 0; }
  }

  /* ─── MAIN CONTENT ─── */
  .container {
    max-width: 960px;
    margin: 0 auto;
    padding: 0 24px;
  }

  section {
    padding: 48px 0;
    border-bottom: 1px solid var(--border);
  }

  /* ─── SECTION HEADERS ─── */
  .section-label {
    font-family: 'Rajdhani', sans-serif;
    font-size: 11px;
    letter-spacing: 0.4em;
    color: var(--red);
    text-transform: uppercase;
    margin-bottom: 8px;
    font-weight: 600;
  }

  .section-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 32px;
    letter-spacing: 0.08em;
    color: var(--white);
    margin-bottom: 32px;
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border-red), transparent);
  }

  /* ─── DRIVER / STINT CARDS ─── */
  .grid-2 {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
  }

  .card {
    background: var(--bg3);
    border: 1px solid var(--border);
    padding: 28px;
    position: relative;
    overflow: hidden;
    transition: border-color 0.3s ease, background 0.3s ease;
  }

  .card:hover {
    border-color: rgba(232,0,28,0.4);
    background: var(--bg4);
  }

  .card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 2px;
    height: 100%;
    background: var(--red);
    opacity: 0;
    transition: opacity 0.3s;
  }

  .card:hover::before { opacity: 1; }

  .card-label {
    font-size: 10px;
    letter-spacing: 0.35em;
    color: var(--red);
    font-weight: 700;
    font-family: 'Rajdhani', sans-serif;
    margin-bottom: 16px;
    text-transform: uppercase;
  }

  .card pre {
    font-size: 12px;
    line-height: 1.9;
    color: var(--grey-light);
    overflow: hidden;
  }

  .card pre .key { color: var(--grey); }
  .card pre .val { color: var(--white); }
  .card pre .red { color: var(--red); }
  .card pre .dim { color: var(--grey); font-size: 11px; }

  blockquote {
    border-left: 2px solid var(--red);
    padding: 10px 16px;
    margin-top: 16px;
    background: rgba(232,0,28,0.05);
    font-size: 12px;
    color: var(--grey-light);
    font-style: italic;
    line-height: 1.7;
  }

  /* ─── STACK GRID ─── */
  .stack-section { text-align: center; }

  .stack-group-label {
    font-family: 'Rajdhani', sans-serif;
    font-size: 11px;
    letter-spacing: 0.4em;
    color: var(--grey);
    text-transform: uppercase;
    margin: 28px 0 14px;
    font-weight: 600;
  }

  .badges {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    justify-content: center;
    margin-bottom: 8px;
  }

  .badge {
    background: var(--bg3);
    border: 1px solid var(--border);
    padding: 8px 18px;
    font-size: 11px;
    letter-spacing: 0.12em;
    font-weight: 600;
    font-family: 'Rajdhani', sans-serif;
    display: flex;
    align-items: center;
    gap: 8px;
    transition: all 0.2s ease;
    cursor: default;
  }

  .badge:hover {
    border-color: var(--red);
    background: rgba(232,0,28,0.08);
    transform: translateY(-2px);
    box-shadow: 0 4px 20px rgba(232,0,28,0.15);
  }

  .badge-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    flex-shrink: 0;
  }

  /* ─── STATS ROW ─── */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    margin-top: 16px;
  }

  .stat-card {
    background: var(--bg3);
    border: 1px solid var(--border);
    padding: 24px;
    text-align: center;
    position: relative;
    overflow: hidden;
    transition: all 0.3s;
  }

  .stat-card:hover {
    border-color: rgba(232,0,28,0.4);
  }

  .stat-number {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 48px;
    color: var(--red);
    letter-spacing: 0.05em;
    line-height: 1;
  }

  .stat-label {
    font-size: 10px;
    letter-spacing: 0.3em;
    color: var(--grey);
    font-family: 'Rajdhani', sans-serif;
    font-weight: 600;
    text-transform: uppercase;
    margin-top: 8px;
  }

  /* ─── STINT GRID ─── */
  .stint-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
  }

  .stint-card {
    background: var(--bg3);
    border: 1px solid var(--border);
    padding: 28px 24px;
    text-align: center;
    transition: all 0.3s;
    cursor: default;
  }

  .stint-card:hover {
    border-color: rgba(232,0,28,0.5);
    background: var(--bg4);
    transform: translateY(-3px);
    box-shadow: 0 12px 40px rgba(232,0,28,0.1);
  }

  .stint-number {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 13px;
    letter-spacing: 0.3em;
    color: var(--red);
    margin-bottom: 12px;
  }

  .stint-title {
    font-family: 'Rajdhani', sans-serif;
    font-size: 16px;
    font-weight: 700;
    letter-spacing: 0.1em;
    margin-bottom: 20px;
    text-transform: uppercase;
  }

  .stint-items {
    list-style: none;
    font-size: 11px;
    color: var(--grey-light);
    line-height: 2;
    text-align: left;
  }

  .stint-items li::before { content: '▸  '; color: var(--red); }

  .progress-row {
    margin-top: 20px;
    font-size: 10px;
    color: var(--grey);
    letter-spacing: 0.2em;
    font-family: 'Rajdhani', sans-serif;
    font-weight: 600;
  }

  .progress-bar {
    width: 100%;
    height: 2px;
    background: var(--border);
    margin-top: 8px;
    position: relative;
    overflow: hidden;
  }

  .progress-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--red-dim), var(--red));
    position: relative;
  }

  .progress-fill::after {
    content: '';
    position: absolute;
    right: 0; top: -2px;
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--red);
    box-shadow: 0 0 6px var(--red);
  }

  /* ─── PIT WALL COMMS ─── */
  .comms {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .comm-line {
    display: flex;
    gap: 16px;
    align-items: flex-start;
    padding: 16px 20px;
    background: var(--bg3);
    border: 1px solid var(--border);
    border-left: 2px solid transparent;
    transition: all 0.3s;
    animation: fadeInUp 0.5s ease both;
  }

  .comm-line.engineer { border-left-color: var(--grey); }
  .comm-line.driver { border-left-color: var(--red); }
  .comm-line:hover { background: var(--bg4); }

  .comm-sender {
    font-family: 'Rajdhani', sans-serif;
    font-weight: 700;
    font-size: 11px;
    letter-spacing: 0.25em;
    white-space: nowrap;
    min-width: 90px;
    padding-top: 2px;
  }

  .comm-sender.engineer-label { color: var(--grey); }
  .comm-sender.driver-label { color: var(--red); }

  .comm-text {
    font-size: 13px;
    color: var(--grey-light);
    line-height: 1.6;
  }

  /* ─── IDENTITY CARD ─── */
  .identity-card {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-top: 2px solid var(--red);
    padding: 28px 32px;
    font-size: 12px;
    line-height: 2.2;
    color: var(--grey-light);
    font-family: 'JetBrains Mono', monospace;
  }

  .identity-card .row {
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .identity-card .icon { color: var(--red); width: 20px; }
  .identity-card .info { color: var(--white); }

  /* ─── CONNECT SECTION ─── */
  .connect-section { text-align: center; }

  .connect-buttons {
    display: flex;
    gap: 12px;
    justify-content: center;
    margin-top: 24px;
    flex-wrap: wrap;
  }

  .connect-btn {
    display: flex;
    align-items: center;
    gap: 10px;
    background: var(--bg3);
    border: 1px solid var(--border);
    padding: 12px 24px;
    font-family: 'Rajdhani', sans-serif;
    font-size: 13px;
    font-weight: 700;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--grey-light);
    text-decoration: none;
    transition: all 0.3s ease;
    cursor: pointer;
  }

  .connect-btn:hover {
    border-color: var(--red);
    color: var(--white);
    background: rgba(232,0,28,0.08);
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(232,0,28,0.2);
  }

  .connect-icon { font-size: 16px; }

  /* ─── FOOTER ─── */
  footer {
    background: var(--bg2);
    border-top: 1px solid var(--border);
    padding: 40px 0;
    text-align: center;
  }

  .footer-ticker {
    font-size: 10px;
    letter-spacing: 0.4em;
    color: var(--grey);
    margin-bottom: 16px;
    font-family: 'Rajdhani', sans-serif;
    font-weight: 600;
    text-transform: uppercase;
  }

  .footer-ticker span { color: var(--red); }

  .footer-sig {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--grey);
    font-style: italic;
  }

  /* ─── ANIMATIONS ─── */
  @keyframes fadeInUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ─── SCROLLBAR ─── */
  ::-webkit-scrollbar { width: 3px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--red); }

  /* ─── CORNER DECORATION ─── */
  .corner-deco {
    position: fixed;
    top: 16px; right: 16px;
    font-family: 'Rajdhani', sans-serif;
    font-size: 10px;
    letter-spacing: 0.3em;
    color: rgba(232,0,28,0.4);
    font-weight: 600;
    text-transform: uppercase;
    pointer-events: none;
    z-index: 100;
  }

  .pulse-dot {
    display: inline-block;
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--red);
    margin-right: 6px;
    animation: pulse 1.2s ease infinite;
    vertical-align: middle;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; box-shadow: 0 0 0 0 rgba(232,0,28,0.4); }
    50% { opacity: 0.6; box-shadow: 0 0 0 4px rgba(232,0,28,0); }
  }
</style>
</head>
<body>

<div class="corner-deco"><span class="pulse-dot"></span>LIVE — GITHUB.COM/JOAOSIMOES</div>

<!-- HERO -->
<div class="hero">
  <div class="hero-stripe"></div>
  <div class="hero-stripe"></div>
  <div class="hero-name">JOÃO <span>SIMÕES</span></div>
  <div class="hero-sub">Software Developer &nbsp;·&nbsp; Aveiro, Portugal</div>
  <div class="hero-badge">
    <div class="hero-pill">CS @ Univ. Aveiro</div>
    <div class="hero-pill">Intern @ COSMO Software</div>
    <div class="hero-pill">Backend · Web · AI</div>
  </div>
</div>

<!-- TELEMETRY TICKER -->
<div class="telemetry-bar">
  <div class="telemetry-ticker">
    <span>◄◄ ONBOARD</span>
    <span>SECTOR 1 ✓</span>
    <span>SECTOR 2 ✓</span>
    <span>SECTOR 3 →</span>
    <span style="color:var(--red)">DRS: OPEN</span>
    <span>GAP TO LEADER: 0.0s</span>
    <span>COMPOUND: SOFT 🔴</span>
    <span>ERS: MAX</span>
    <span style="color:var(--red)">PUSH NOW</span>
    <span>◄◄ ONBOARD</span>
    <span>SECTOR 1 ✓</span>
    <span>SECTOR 2 ✓</span>
    <span>SECTOR 3 →</span>
    <span style="color:var(--red)">DRS: OPEN</span>
    <span>GAP TO LEADER: 0.0s</span>
    <span>COMPOUND: SOFT 🔴</span>
    <span>ERS: MAX</span>
    <span style="color:var(--red)">PUSH NOW</span>
  </div>
</div>

<!-- TYPING DISPLAY -->
<div class="typing-display">
  <div class="typing-line" id="typingLine">_ Transforming complex problems into efficient solutions</div>
</div>

<div class="container">

  <!-- DRIVER PROFILE + CURRENT LAP -->
  <section>
    <div class="section-label">Systems Online</div>
    <div class="section-title">Driver Profile</div>
    <div class="grid-2">

      <div class="card">
        <div class="card-label">◈ Driver Data</div>
        <pre>
<span class="key">Driver     </span><span class="red">:</span> <span class="val">João Simões</span>
<span class="key">Number     </span><span class="red">:</span> <span class="val">#01</span>
<span class="key">Team       </span><span class="red">:</span> <span class="val">COSMO Software</span>
<span class="key">Base       </span><span class="red">:</span> <span class="val">Aveiro, Portugal 🇵🇹</span>
<span class="key">Academy    </span><span class="red">:</span> <span class="val">University of Aveiro — CS</span>
<span class="key">Season     </span><span class="red">:</span> <span class="val">2025 → ongoing</span>

<span class="key">Speciality </span><span class="red">:</span> <span class="val">Backend Systems</span>
             <span class="val">Web Development</span>
             <span class="val">Automation &amp; AI</span>

<span class="key">Mindset    </span><span class="red">:</span> <span class="val">Ambitious · Creative · Relentless</span>
        </pre>
      </div>

      <div class="card">
        <div class="card-label">◎ Current Lap</div>
        <pre>
<span class="key">RACE POSITION  </span><span class="red">→</span>  <span class="val">Evolving daily</span>
<span class="key">CURRENT STINT  </span><span class="red">→</span>  <span class="val">Software Dev Intern</span>
<span class="key">COMPOUND       </span><span class="red">→</span>  <span class="val">SOFT 🔴  (Attack mode)</span>
<span class="key">FUEL LOAD      </span><span class="red">→</span>  <span class="val">████████████░░  87%</span>
<span class="key">ERS DEPLOYMENT </span><span class="red">→</span>  <span class="val">██████████████ MAX</span>
        </pre>
        <blockquote>
          "The best engineers don't just write code —<br>
          they engineer outcomes."
        </blockquote>
      </div>

    </div>
  </section>

  <!-- ENGINEERING STACK -->
  <section class="stack-section">
    <div class="section-label">Technical Specification</div>
    <div class="section-title">Engineering Stack</div>

    <div class="stack-group-label">— Languages —</div>
    <div class="badges">
      <div class="badge"><div class="badge-dot" style="background:#8892BF"></div>PHP</div>
      <div class="badge"><div class="badge-dot" style="background:#F7DF1E"></div>JavaScript</div>
      <div class="badge"><div class="badge-dot" style="background:#E34F26"></div>HTML5</div>
      <div class="badge"><div class="badge-dot" style="background:#1572B6"></div>CSS3</div>
      <div class="badge"><div class="badge-dot" style="background:#4169E1"></div>SQL</div>
    </div>

    <div class="stack-group-label">— Frameworks &amp; Runtime —</div>
    <div class="badges">
      <div class="badge"><div class="badge-dot" style="background:#61DAFB"></div>React</div>
      <div class="badge"><div class="badge-dot" style="background:#339933"></div>Node.js</div>
      <div class="badge"><div class="badge-dot" style="background:#FFFFFF"></div>Express</div>
    </div>

    <div class="stack-group-label">— Tools &amp; Infrastructure —</div>
    <div class="badges">
      <div class="badge"><div class="badge-dot" style="background:#F05032"></div>Git</div>
      <div class="badge"><div class="badge-dot" style="background:#FFFFFF"></div>GitHub</div>
      <div class="badge"><div class="badge-dot" style="background:#2496ED"></div>Docker</div>
      <div class="badge"><div class="badge-dot" style="background:#4479A1"></div>MySQL</div>
      <div class="badge"><div class="badge-dot" style="background:#007ACC"></div>VS Code</div>
    </div>

    <div class="stats-row" style="margin-top:40px">
      <div class="stat-card">
        <div class="stat-number">5+</div>
        <div class="stat-label">Languages in Stack</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">∞</div>
        <div class="stat-label">Problems to Solve</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">01</div>
        <div class="stat-label">Driver Number</div>
      </div>
    </div>
  </section>

  <!-- RACE STRATEGY / STINTS -->
  <section>
    <div class="section-label">2025 Season Plan</div>
    <div class="section-title">Race Strategy</div>
    <div class="stint-grid">

      <div class="stint-card">
        <div class="stint-number">◈ STINT 01</div>
        <div class="stint-title">Backend Mastery</div>
        <ul class="stint-items">
          <li>REST API Architecture</li>
          <li>Database Optimization</li>
          <li>Server-side Performance</li>
          <li>Clean Code Principles</li>
          <li>System Design Thinking</li>
        </ul>
        <div class="progress-row">IN PROGRESS</div>
        <div class="progress-bar"><div class="progress-fill" style="width:85%"></div></div>
      </div>

      <div class="stint-card">
        <div class="stint-number">◈ STINT 02</div>
        <div class="stint-title">Full-Stack Depth</div>
        <ul class="stint-items">
          <li>React Ecosystem</li>
          <li>Node.js / Express</li>
          <li>Docker &amp; Containers</li>
          <li>CI/CD Pipelines</li>
          <li>Scalable Architecture</li>
        </ul>
        <div class="progress-row">IN PROGRESS</div>
        <div class="progress-bar"><div class="progress-fill" style="width:68%"></div></div>
      </div>

      <div class="stint-card">
        <div class="stint-number">◈ STINT 03</div>
        <div class="stint-title">Intelligence Layer</div>
        <ul class="stint-items">
          <li>AI Integration</li>
          <li>Automation Systems</li>
          <li>Machine Learning Basics</li>
          <li>LLM APIs &amp; Tooling</li>
          <li>Intelligent Backends</li>
        </ul>
        <div class="progress-row">INCOMING</div>
        <div class="progress-bar"><div class="progress-fill" style="width:42%"></div></div>
      </div>

    </div>
  </section>

  <!-- PIT WALL COMMS -->
  <section>
    <div class="section-label">Race Control</div>
    <div class="section-title">Pit Wall — Live Comms</div>
    <div class="comms">

      <div class="comm-line engineer" style="animation-delay:0.1s">
        <div class="comm-sender engineer-label">ENGINEER →</div>
        <div class="comm-text">"João, you're currently P1 on long-run pace. Keep pushing."</div>
      </div>

      <div class="comm-line driver" style="animation-delay:0.3s">
        <div class="comm-sender driver-label">JOÃO →</div>
        <div class="comm-text">"Copy. The backend is clean, we have pace. Let's attack."</div>
      </div>

      <div class="comm-line engineer" style="animation-delay:0.5s">
        <div class="comm-sender engineer-label">ENGINEER →</div>
        <div class="comm-text">"New sector personal best — purple. Excellent work."</div>
      </div>

      <div class="comm-line driver" style="animation-delay:0.7s">
        <div class="comm-sender driver-label">JOÃO →</div>
        <div class="comm-text">"It's not about the fast lap. It's about consistent performance across the whole race."</div>
      </div>

    </div>

    <div class="identity-card" style="margin-top:32px">
      <div class="row"><span class="icon">🎓</span><span>CS @ University of Aveiro</span><span style="color:var(--grey);margin-left:auto">Aveiro, Portugal 🇵🇹</span></div>
      <div class="row"><span class="icon">💼</span><span class="info">Software Developer Intern @ COSMO Software</span></div>
      <div class="row"><span class="icon">⚡</span><span>Backend · Web · Automation · AI</span></div>
      <div class="row"><span class="icon">🎯</span><span>Obsessed with elegant, efficient solutions</span></div>
      <div class="row"><span class="icon">🔧</span><span>Currently building: production-grade systems</span></div>
      <div class="row"><span class="icon">📡</span><span style="color:var(--grey-light)">Always learning. Always improving. Never settling.</span></div>
    </div>
  </section>

  <!-- CONNECT -->
  <section class="connect-section" style="border-bottom:none">
    <div class="section-label">Contact Interface</div>
    <div class="section-title" style="justify-content:center">Open Channel</div>
    <div class="connect-buttons">
      <div class="connect-btn">
        <span class="connect-icon">in</span>
        <span>LinkedIn</span>
      </div>
      <div class="connect-btn">
        <span class="connect-icon">✉</span>
        <span>Direct Radio</span>
      </div>
      <div class="connect-btn">
        <span class="connect-icon">⌥</span>
        <span>GitHub</span>
      </div>
    </div>
  </section>

</div>

<!-- FOOTER -->
<footer>
  <div class="footer-ticker">
    <span class="pulse-dot"></span>
    TRANSMISSION ENDED &nbsp;·&nbsp; LAP COMPLETE &nbsp;·&nbsp; &nbsp;<span>J.S. // 2025</span>
  </div>
  <div class="footer-sig">// Precision. Speed. Evolution. — J.S.</div>
</footer>

<script>
  // Typing effect cycle
  const lines = [
    "_ Transforming complex problems into efficient solutions",
    "_ Software Developer Intern @ COSMO Software",
    "_ Backend · Web · Automation · AI",
    "_ University of Aveiro — Computer Science",
    "_ Always learning. Always improving. Never settling."
  ];
  let i = 0;
  const el = document.getElementById('typingLine');
  
  function cycleLine() {
    el.style.opacity = '0';
    setTimeout(() => {
      i = (i + 1) % lines.length;
      el.textContent = lines[i];
      el.style.transition = 'opacity 0.5s ease';
      el.style.opacity = '1';
    }, 500);
  }
  
  setInterval(cycleLine, 3500);
  el.style.opacity = '1';
</script>

</body>
</html>
