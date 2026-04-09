<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sidhartha Priyadarshi - Marketing Portfolio</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Syne:wght@400;500;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --ink: #0e0c0a;
    --cream: #f2ede6;
    --warm: #c8a97e;
    --rust: #b5451b;
    --mist: #1a1714;
    --card: #161310;
    --border: rgba(200,169,126,0.18);
    --text-muted: rgba(242,237,230,0.45);
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--ink);
    color: var(--cream);
    font-family: 'Syne', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }
  /* Custom cursor */
  .cursor {
    position: fixed; width: 10px; height: 10px;
    background: var(--warm); border-radius: 50%;
    pointer-events: none; z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s ease, width 0.3s ease, height 0.3s ease, opacity 0.3s ease;
    mix-blend-mode: screen;
  }
  .cursor-ring {
    position: fixed; width: 36px; height: 36px;
    border: 1px solid rgba(200,169,126,0.5); border-radius: 50%;
    pointer-events: none; z-index: 9998;
    transform: translate(-50%, -50%);
    transition: transform 0.18s ease, width 0.3s ease, height 0.3s ease;
  }
  body:hover .cursor { opacity: 1; }

  /* Noise texture overlay */
  body::before {
    content: ''; position: fixed; inset: 0; z-index: 1000;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.035'/%3E%3C/svg%3E");
    pointer-events: none; opacity: 0.6;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.4rem 3rem;
    border-bottom: 1px solid var(--border);
    background: rgba(14,12,10,0.85);
    backdrop-filter: blur(12px);
  }
  .nav-logo {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.35rem; font-weight: 300; letter-spacing: 0.08em;
    color: var(--cream); text-decoration: none;
  }
  .nav-logo span { color: var(--warm); font-style: italic; }
  .nav-links { display: flex; gap: 2.5rem; list-style: none; }
  .nav-links a {
    font-size: 0.72rem; letter-spacing: 0.2em; text-transform: uppercase;
    color: var(--text-muted); text-decoration: none;
    transition: color 0.25s;
  }
  .nav-links a:hover { color: var(--warm); }

  /* HERO */
  .hero {
    min-height: 100vh; display: flex; flex-direction: column;
    justify-content: flex-end; padding: 0 3rem 5rem;
    position: relative; overflow: hidden;
  }
  .hero-bg {
    position: absolute; inset: 0;
    background: radial-gradient(ellipse 80% 60% at 70% 40%, rgba(181,69,27,0.08) 0%, transparent 65%),
                radial-gradient(ellipse 60% 80% at 10% 80%, rgba(200,169,126,0.05) 0%, transparent 60%);
  }
  .hero-number {
    position: absolute; top: 50%; right: 3rem;
    transform: translateY(-50%);
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(14rem, 22vw, 22rem);
    font-weight: 300; line-height: 1;
    color: rgba(200,169,126,0.04);
    letter-spacing: -0.05em;
    user-select: none; pointer-events: none;
  }
  .hero-tag {
    font-size: 0.7rem; letter-spacing: 0.28em; text-transform: uppercase;
    color: var(--warm); margin-bottom: 1.8rem;
    opacity: 0; animation: fadeUp 0.8s 0.2s forwards;
  }
  .hero h1 {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(3.8rem, 9vw, 8.5rem);
    font-weight: 300; line-height: 1.02;
    letter-spacing: -0.02em;
    opacity: 0; animation: fadeUp 0.9s 0.4s forwards;
  }
  .hero h1 em { font-style: italic; color: var(--warm); }
  .hero-sub {
    margin-top: 1.8rem; max-width: 480px;
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.2rem; font-weight: 300; line-height: 1.7;
    color: rgba(242,237,230,0.6);
    opacity: 0; animation: fadeUp 0.9s 0.6s forwards;
  }
  .hero-cta {
    margin-top: 3rem; display: flex; gap: 1.5rem; align-items: center;
    opacity: 0; animation: fadeUp 0.9s 0.8s forwards;
  }
  .btn-primary {
    display: inline-flex; align-items: center; gap: 0.6rem;
    padding: 0.85rem 2rem;
    background: var(--warm); color: var(--ink);
    font-family: 'Syne', sans-serif; font-size: 0.72rem;
    font-weight: 700; letter-spacing: 0.18em; text-transform: uppercase;
    text-decoration: none; transition: all 0.3s;
  }
  .btn-primary:hover { background: var(--cream); transform: translateY(-2px); }
  .btn-ghost {
    font-size: 0.72rem; letter-spacing: 0.2em; text-transform: uppercase;
    color: var(--text-muted); text-decoration: none;
    border-bottom: 1px solid var(--border); padding-bottom: 2px;
    transition: color 0.25s, border-color 0.25s;
  }
  .btn-ghost:hover { color: var(--cream); border-color: var(--cream); }

  .hero-scroll {
    position: absolute; bottom: 2.5rem; right: 3rem;
    display: flex; flex-direction: column; align-items: center; gap: 0.5rem;
    font-size: 0.65rem; letter-spacing: 0.22em; text-transform: uppercase;
    color: var(--text-muted);
  }
  .scroll-line {
    width: 1px; height: 48px;
    background: linear-gradient(to bottom, var(--warm), transparent);
    animation: scrollPulse 2s ease-in-out infinite;
  }

  /* SECTIONS */
  section { padding: 7rem 3rem; }
  .section-header {
    display: flex; align-items: baseline; gap: 1.5rem;
    margin-bottom: 4rem; border-bottom: 1px solid var(--border);
    padding-bottom: 1.5rem;
  }
  .section-num {
    font-family: 'Cormorant Garamond', serif;
    font-size: 0.9rem; font-style: italic; color: var(--warm);
  }
  .section-title {
    font-family: 'Syne', sans-serif; font-size: 0.72rem;
    font-weight: 700; letter-spacing: 0.25em; text-transform: uppercase;
    color: var(--cream);
  }
  .section-rule { flex: 1; height: 1px; background: transparent; }

  /* ABOUT */
  #about { background: var(--mist); }
  .about-grid {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 5rem; align-items: start;
  }
  .about-statement {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(1.8rem, 3vw, 2.6rem);
    font-weight: 300; line-height: 1.45;
    color: var(--cream);
  }
  .about-statement em { font-style: italic; color: var(--warm); }
  .about-details { display: flex; flex-direction: column; gap: 2.5rem; }
  .about-item label {
    display: block; font-size: 0.65rem; letter-spacing: 0.2em;
    text-transform: uppercase; color: var(--warm); margin-bottom: 0.5rem;
  }
  .about-item p {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.05rem; line-height: 1.7;
    color: rgba(242,237,230,0.7);
  }
  .expertise-chips {
    display: flex; flex-wrap: wrap; gap: 0.6rem; margin-top: 0.8rem;
  }
  .chip {
    font-size: 0.65rem; letter-spacing: 0.15em; text-transform: uppercase;
    padding: 0.3rem 0.8rem; border: 1px solid var(--border);
    color: var(--text-muted); transition: all 0.25s;
  }
  .chip:hover { border-color: var(--warm); color: var(--warm); }

  /* WORK */
  #work { background: var(--ink); }
  .brand-block { margin-bottom: 5rem; }
  .brand-header {
    display: flex; align-items: center; gap: 1.5rem;
    margin-bottom: 2rem;
  }
  .brand-name {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2.4rem; font-weight: 300; letter-spacing: -0.01em;
  }
  .brand-tag {
    font-size: 0.65rem; letter-spacing: 0.2em; text-transform: uppercase;
    color: var(--warm); padding: 0.25rem 0.7rem;
    border: 1px solid rgba(200,169,126,0.3);
  }
  .brand-divider {
    flex: 1; height: 1px;
    background: linear-gradient(to right, var(--border), transparent);
  }

  .cards-grid {
    display: grid; gap: 1px;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    background: var(--border);
  }
  .work-card {
    background: var(--card); padding: 1.6rem;
    text-decoration: none; color: var(--cream);
    display: flex; flex-direction: column; gap: 0.8rem;
    transition: background 0.25s;
    position: relative; overflow: hidden;
  }
  .work-card::before {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(200,169,126,0.07) 0%, transparent 60%);
    opacity: 0; transition: opacity 0.35s;
  }
  .work-card:hover { background: #1e1a16; }
  .work-card:hover::before { opacity: 1; }
  .card-type {
    font-size: 0.6rem; letter-spacing: 0.22em; text-transform: uppercase;
    color: var(--warm);
  }
  .card-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.15rem; line-height: 1.4;
    color: var(--cream);
  }
  .card-arrow {
    margin-top: auto; font-size: 0.75rem; color: var(--text-muted);
    transition: color 0.25s, transform 0.25s;
    display: flex; align-items: center; gap: 0.4rem;
  }
  .work-card:hover .card-arrow { color: var(--warm); transform: translateX(4px); }
  .card-thumb {
    width: 100%; aspect-ratio: 16/9; background: #1a1714;
    overflow: hidden; position: relative;
  }
  .card-thumb img { width: 100%; height: 100%; object-fit: cover; opacity: 0.7; transition: opacity 0.3s; }
  .work-card:hover .card-thumb img { opacity: 1; }
  .yt-thumb { width: 100%; aspect-ratio: 16/9; position: relative; overflow: hidden; }
  .yt-thumb img { width: 100%; height: 100%; object-fit: cover; opacity: 0.65; transition: opacity 0.35s ease; }
  .work-card:hover .yt-thumb img { opacity: 0.9; }
  .yt-play {
    position: absolute; top: 50%; left: 50%; transform: translate(-50%,-50%);
    width: 40px; height: 40px; border-radius: 50%;
    background: rgba(200,169,126,0.85); display: flex; align-items: center; justify-content: center;
    transition: background 0.25s, transform 0.25s;
  }
  .work-card:hover .yt-play { background: var(--warm); transform: translate(-50%,-50%) scale(1.1); }
  .yt-play svg { fill: var(--ink); width: 14px; margin-left: 2px; }

  /* PR card */
  .pr-card {
    background: var(--card); padding: 1.4rem 1.6rem;
    text-decoration: none; color: var(--cream);
    display: flex; align-items: flex-start; gap: 1rem;
    transition: background 0.25s; border-bottom: 1px solid var(--border);
  }
  .pr-card:hover { background: #1e1a16; }
  .pr-num {
    font-family: 'Cormorant Garamond', serif;
    font-size: 0.85rem; color: var(--warm); min-width: 2rem; margin-top: 0.1rem;
  }
  .pr-body { flex: 1; }
  .pr-source {
    font-size: 0.6rem; letter-spacing: 0.18em; text-transform: uppercase;
    color: var(--text-muted); margin-bottom: 0.3rem;
  }
  .pr-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.05rem; line-height: 1.45; color: var(--cream);
  }
  .pr-arrow { font-size: 0.8rem; color: var(--text-muted); margin-top: 0.15rem; transition: color 0.2s; }
  .pr-card:hover .pr-arrow { color: var(--warm); }
  .pr-list { border-top: 1px solid var(--border); }

  /* CONTACT */
  #contact {
    background: var(--mist);
    min-height: 60vh; display: flex; flex-direction: column;
    justify-content: center;
  }
  .contact-inner { max-width: 680px; }
  .contact-eyebrow {
    font-size: 0.68rem; letter-spacing: 0.25em; text-transform: uppercase;
    color: var(--warm); margin-bottom: 1.5rem;
  }
  .contact-heading {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(2.8rem, 6vw, 5.5rem);
    font-weight: 300; line-height: 1.1; margin-bottom: 2.5rem;
  }
  .contact-heading em { font-style: italic; color: var(--warm); }
  .contact-links { display: flex; gap: 2rem; flex-wrap: wrap; }
  .contact-link {
    display: flex; align-items: center; gap: 0.6rem;
    font-size: 0.72rem; letter-spacing: 0.18em; text-transform: uppercase;
    color: var(--text-muted); text-decoration: none;
    border-bottom: 1px solid var(--border); padding-bottom: 3px;
    transition: all 0.25s;
  }
  .contact-link:hover { color: var(--warm); border-color: var(--warm); }

  footer {
    padding: 2rem 3rem;
    border-top: 1px solid var(--border);
    display: flex; justify-content: space-between; align-items: center;
    font-size: 0.65rem; letter-spacing: 0.15em; text-transform: uppercase;
    color: var(--text-muted);
  }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(28px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes scrollPulse {
    0%, 100% { opacity: 0.4; } 50% { opacity: 1; }
  }

  .reveal {
    opacity: 0; transform: translateY(24px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }
  .reveal-delay-1 { transition-delay: 0.1s; }
  .reveal-delay-2 { transition-delay: 0.2s; }
  .reveal-delay-3 { transition-delay: 0.3s; }

  /* RESPONSIVE */
  @media (max-width: 768px) {
    nav { padding: 1.2rem 1.5rem; }
    .nav-links { display: none; }
    section { padding: 5rem 1.5rem; }
    .hero { padding: 0 1.5rem 4rem; }
    .about-grid { grid-template-columns: 1fr; gap: 3rem; }
    .cards-grid { grid-template-columns: 1fr; }
    footer { flex-direction: column; gap: 1rem; text-align: center; }
    .hero-number { display: none; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>
<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">Sidhartha <span>Priyadarshi</span></a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#work">Work</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>
<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-bg"></div>
  <div class="hero-number">SP</div>
  <p class="hero-tag">Marketing Portfolio</p>
  <h2>Brand, Comm &amp; <em>Growth</em>Marketing Lead</h2>
  <p class="hero-sub">FMCG · Retail · Real Estate · Hospitality - building brands that resonate, campaigns that convert, and stories that endure.</p>
  <div class="hero-cta">
    <a href="#work" class="btn-primary">View Work ↓</a>
    <a href="#contact" class="btn-ghost">Get in Touch</a>
  </div>
  <div class="hero-scroll">
    <div class="scroll-line"></div>
    <span>Scroll</span>
  </div>
</section>
<!-- ABOUT -->
<section id="about">
  <div class="section-header reveal">
    <span class="section-num">01</span>
    <span class="section-title">About</span>
  </div>
  <div class="about-grid">
    <div class="about-statement reveal">
      A marketer who lives at the intersection of <em>brand narrative</em> and performance - from zero-to-one launches to scaling established equity.
    </div>
    <div class="about-details">
      <div class="about-item reveal reveal-delay-1">
        <label>Background</label>
        <p>Senior marketing leader with a track record across FMCG, retail fashion, and commercial real estate. Built brands, led GTM launches, and driven performance marketing across Meta and Google.</p>
      </div>
      <div class="about-item reveal reveal-delay-2">
        <label>Expertise</label>
        <div class="expertise-chips">
          <span class="chip">Brand Strategy</span>
          <span class="chip">TVC Production</span>
          <span class="chip">Performance Marketing</span>
          <span class="chip">PR &amp; Comms</span>
          <span class="chip">GTM Launch</span>
          <span class="chip">D2C</span>
          <span class="chip">Content</span>
          <span class="chip">Digital</span>
        </div>
      </div>
      <div class="about-item reveal reveal-delay-3">
        <label>Industries</label>
        <p>FMCG (Unibic Cookies, Dukes Waffy) · Hospitality (Rajdhani, Rasovara, Cafe Mangii, Socials)· Dairy (MilkLane) · Retail Grocery & Fashion (Reliance Retail / Landmark Group) · Commercial Real Estate (IndiQube)</p>
      </div>
    </div>
  </div>
</section>
<!-- WORK -->
<section id="work">
  <div class="section-header reveal">
    <span class="section-num">02</span>
    <span class="section-title">Selected Work</span>
  </div>
  <!-- UNIBIC -->
  <div class="brand-block reveal">
    <div class="brand-header">
      <span class="brand-name">Unibic</span>
      <span class="brand-tag">FMCG · Biscuits</span>
      <div class="brand-divider"></div>
    </div>
    <p style="font-family:'Cormorant Garamond',serif;font-size:1rem;color:var(--text-muted);margin-bottom:1.8rem;line-height:1.7;">Television commercials crafted to build brand salience in India's competitive biscuit category.</p>
    <div class="cards-grid">
      <!-- TVC 1 -->
      <a href="https://www.youtube.com/watch?v=SMYRh52p1HE" target="_blank" class="work-card">
        <div class="yt-thumb">
          <img src="https://img.youtube.com/vi/SMYRh52p1HE/mqdefault.jpg" alt="Unibic TVC">
          <div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div>
        </div>
        <span class="card-type">TVC</span>
        <p class="card-title">Unibic - Brand Commercial #1</p>
        <span class="card-arrow">Watch on YouTube →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=BAZoOoLMbW4" target="_blank" class="work-card">
        <div class="yt-thumb">
          <img src="https://img.youtube.com/vi/BAZoOoLMbW4/mqdefault.jpg" alt="Unibic TVC">
          <div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div>
        </div>
        <span class="card-type">TVC</span>
        <p class="card-title">Unibic - Brand Commercial #2</p>
        <span class="card-arrow">Watch on YouTube →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=lD4mjPrpYwo" target="_blank" class="work-card">
        <div class="yt-thumb">
          <img src="https://img.youtube.com/vi/lD4mjPrpYwo/mqdefault.jpg" alt="Unibic TVC">
          <div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div>
        </div>
        <span class="card-type">TVC</span>
        <p class="card-title">Unibic - Brand Commercial #3</p>
        <span class="card-arrow">Watch on YouTube →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=9If2Kkdx5zQ" target="_blank" class="work-card">
        <div class="yt-thumb">
          <img src="https://img.youtube.com/vi/9If2Kkdx5zQ/mqdefault.jpg" alt="Unibic TVC">
          <div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div>
        </div>
        <span class="card-type">TVC</span>
        <p class="card-title">Unibic - Brand Commercial #4</p>
        <span class="card-arrow">Watch on YouTube →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=Sd5I7sirVJc" target="_blank" class="work-card">
        <div class="yt-thumb">
          <img src="https://img.youtube.com/vi/Sd5I7sirVJc/mqdefault.jpg" alt="Unibic TVC">
          <div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div>
        </div>
        <span class="card-type">TVC</span>
        <p class="card-title">Unibic - Brand Commercial #5</p>
        <span class="card-arrow">Watch on YouTube →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=ITcTkx_h1Wc" target="_blank" class="work-card">
        <div class="yt-thumb">
          <img src="https://img.youtube.com/vi/ITcTkx_h1Wc/mqdefault.jpg" alt="Unibic TVC">
          <div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div>
        </div>
        <span class="card-type">TVC</span>
        <p class="card-title">Unibic - Brand Commercial #6</p>
        <span class="card-arrow">Watch on YouTube →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=_SmN9ttNfhc" target="_blank" class="work-card">
        <div class="yt-thumb">
          <img src="https://img.youtube.com/vi/_SmN9ttNfhc/mqdefault.jpg" alt="Unibic TVC">
          <div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div>
        </div>
        <span class="card-type">TVC</span>
        <p class="card-title">Unibic - Brand Commercial #7</p>
        <span class="card-arrow">Watch on YouTube →</span>
      </a>
    </div>
  </div>
  <!-- MILKLANE -->
  <div class="brand-block reveal">
    <div class="brand-header">
      <span class="brand-name">MilkLane</span>
      <span class="brand-tag">Dairy · D2C</span>
      <div class="brand-divider"></div>
    </div>
    <p style="font-family:'Cormorant Garamond',serif;font-size:1rem;color:var(--text-muted);margin-bottom:1.8rem;line-height:1.7;">Brand films establishing identity and emotional resonance for a premium dairy brand.</p>
    <div class="cards-grid">
      <a href="https://www.youtube.com/watch?v=ZzbXQv26EXM" target="_blank" class="work-card">
        <div class="yt-thumb">
          <img src="https://img.youtube.com/vi/ZzbXQv26EXM/mqdefault.jpg" alt="MilkLane Brand Film">
          <div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div>
        </div>
        <span class="card-type">Brand Film</span>
        <p class="card-title">MilkLane - Brand Story Film #1</p>
        <span class="card-arrow">Watch on YouTube →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=UUOnPTGMbQ8" target="_blank" class="work-card">
        <div class="yt-thumb">
          <img src="https://img.youtube.com/vi/UUOnPTGMbQ8/mqdefault.jpg" alt="MilkLane Brand Film">
          <div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div>
        </div>
        <span class="card-type">Brand Film</span>
        <p class="card-title">MilkLane - Brand Story Film #2</p>
        <span class="card-arrow">Watch on YouTube →</span>
      </a>
    </div>
  </div>
  <!-- EASYBUY -->
  <div class="brand-block reveal">
    <div class="brand-header">
      <span class="brand-name">EasyBuy</span>
      <span class="brand-tag">Retail Fashion · Landmark Group</span>
      <div class="brand-divider"></div>
    </div>
    <p style="font-family:'Cormorant Garamond',serif;font-size:1rem;color:var(--text-muted);margin-bottom:1.8rem;line-height:1.7;">NSO launches, digital TVCs, and PR coverage for Landmark Group's value fashion retail chain across India.</p>
    <p style="font-size:0.65rem;letter-spacing:0.2em;text-transform:uppercase;color:var(--warm);margin-bottom:1rem;">Digital TVCs</p>
    <div class="cards-grid" style="margin-bottom:2.5rem;">
      <a href="https://www.youtube.com/watch?v=GIRSiv3_Ydk" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/GIRSiv3_Ydk/mqdefault.jpg" alt="EasyBuy"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Digital TVC</span><p class="card-title">EasyBuy - Digital Campaign #1</p>
        <span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=HyBm-Fu75uw" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/HyBm-Fu75uw/mqdefault.jpg" alt="EasyBuy"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Digital TVC</span><p class="card-title">EasyBuy - Digital Campaign #2</p>
        <span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=b3_e3Srzwmc" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/b3_e3Srzwmc/mqdefault.jpg" alt="EasyBuy"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Digital TVC</span><p class="card-title">EasyBuy - Digital Campaign #3</p>
        <span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=1M-8JQDjyso" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/1M-8JQDjyso/mqdefault.jpg" alt="EasyBuy"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Digital TVC</span><p class="card-title">EasyBuy - Digital Campaign #4</p>
        <span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=hB1n9lIxfxk" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/hB1n9lIxfxk/mqdefault.jpg" alt="EasyBuy"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Digital TVC</span><p class="card-title">EasyBuy - Digital Campaign #5</p>
        <span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=CMkbgeV_IOQ" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/CMkbgeV_IOQ/mqdefault.jpg" alt="EasyBuy"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Digital TVC</span><p class="card-title">EasyBuy - Digital Campaign #6</p>
        <span class="card-arrow">Watch →</span>
      </a>
    </div>
    <p style="font-size:0.65rem;letter-spacing:0.2em;text-transform:uppercase;color:var(--warm);margin-bottom:1rem;">PR Coverage</p>
    <div class="pr-list">
      <a href="https://www.indianretailer.com/news/landmark-groups-easybuy-lights-dharmapuri-32nd-store-steals-retail-spotlight" target="_blank" class="pr-card">
        <span class="pr-num">01</span>
        <div class="pr-body">
          <div class="pr-source">Indian Retailer</div>
          <div class="pr-title">EasyBuy Lights Up Dharmapuri - 32nd Store Launch</div>
        </div>
        <span class="pr-arrow">↗</span>
      </a>
      <a href="https://www.imagesbof.in/easybuy-expands-its-presence-with-new-outlet-in-dharmapuri/" target="_blank" class="pr-card">
        <span class="pr-num">02</span>
        <div class="pr-body">
          <div class="pr-source">Images BoF</div>
          <div class="pr-title">EasyBuy Expands Presence with New Outlet in Dharmapuri</div>
        </div>
        <span class="pr-arrow">↗</span>
      </a>
      <a href="https://www.mediainfoline.com/brand/easybuy-expands-its-presence-with-a-new-look-exclusive-outlet-in-dharmapuri" target="_blank" class="pr-card">
        <span class="pr-num">03</span>
        <div class="pr-body">
          <div class="pr-source">Media Infoline</div>
          <div class="pr-title">EasyBuy - New-Look Exclusive Outlet in Dharmapuri</div>
        </div>
        <span class="pr-arrow">↗</span>
      </a>
      <a href="https://www.youtube.com/watch?v=96gn8esAZS0" target="_blank" class="pr-card">
        <span class="pr-num">04</span>
        <div class="pr-body">
          <div class="pr-source">YouTube · Store Launch</div>
          <div class="pr-title">EasyBuy Store Launch Coverage Video</div>
        </div>
        <span class="pr-arrow">↗</span>
      </a>
    </div>
  </div>
  <!-- INDIQUBE -->
  <div class="brand-block reveal">
    <div class="brand-header">
      <span class="brand-name">IndiQube</span>
      <span class="brand-tag">Commercial Real Estate</span>
      <div class="brand-divider"></div>
    </div>
    <p style="font-family:'Cormorant Garamond',serif;font-size:1rem;color:var(--text-muted);margin-bottom:1.8rem;line-height:1.7;">Full-funnel brand marketing - web, PR, thought leadership, and video collaborations for one of India's fastest-growing workspace companies.</p>
    <p style="font-size:0.65rem;letter-spacing:0.2em;text-transform:uppercase;color:var(--warm);margin-bottom:1rem;">Web &amp; Brand Pages</p>
    <div class="cards-grid" style="margin-bottom:2.5rem;">
      <a href="https://indiqube.com/rishi-das-indiqube/" target="_blank" class="work-card">
        <span class="card-type">Web</span>
        <p class="card-title">Founder Profile - Rishi Das</p>
        <span class="card-arrow">View Page →</span>
      </a>
      <a href="https://indiqube.com/meghna-agarwal-indiqube/" target="_blank" class="work-card">
        <span class="card-type">Web</span>
        <p class="card-title">Founder Profile - Meghna Agarwal</p>
        <span class="card-arrow">View Page →</span>
      </a>
      <a href="https://indiqube.com/officefurniture/" target="_blank" class="work-card">
        <span class="card-type">Web</span>
        <p class="card-title">Office Furniture Product Page</p>
        <span class="card-arrow">View Page →</span>
      </a>
      <a href="https://indiqube.com/investor/" target="_blank" class="work-card">
        <span class="card-type">Web</span>
        <p class="card-title">Investor Relations Page</p>
        <span class="card-arrow">View Page →</span>
      </a>
      <a href="https://indiqube.com/solar/" target="_blank" class="work-card">
        <span class="card-type">Web</span>
        <p class="card-title">Solar / Sustainability Page</p>
        <span class="card-arrow">View Page →</span>
      </a>
    </div>
    <p style="font-size:0.65rem;letter-spacing:0.2em;text-transform:uppercase;color:var(--warm);margin-bottom:1rem;">PR &amp; Media Coverage</p>
    <div class="pr-list" style="margin-bottom:2.5rem;">
      <a href="https://www.fortuneindia.com/rankings/most-powerful-women/2025" target="_blank" class="pr-card">
        <span class="pr-num">01</span>
        <div class="pr-body"><div class="pr-source">Fortune India</div><div class="pr-title">Most Powerful Women 2025 - IndiQube Founder Featured</div></div>
        <span class="pr-arrow">↗</span>
      </a>
      <a href="https://www.financialexpress.com/business/industry-the-big-idea-indiqube-4016457/" target="_blank" class="pr-card">
        <span class="pr-num">02</span>
        <div class="pr-body"><div class="pr-source">Financial Express</div><div class="pr-title">The Big Idea - IndiQube</div></div>
        <span class="pr-arrow">↗</span>
      </a>
      <a href="https://yourstory.com/2025/11/record-revenues-rising-profitability-expanding-cities-indiqube-delivers-breakout-quarter" target="_blank" class="pr-card">
        <span class="pr-num">03</span>
        <div class="pr-body"><div class="pr-source">YourStory</div><div class="pr-title">Record Revenues &amp; Rising Profitability - IndiQube Breakout Quarter</div></div>
        <span class="pr-arrow">↗</span>
      </a>
      <a href="https://indiqube.com/indiqube-founders-hurun-india-top-200-2025/" target="_blank" class="pr-card">
        <span class="pr-num">04</span>
        <div class="pr-body"><div class="pr-source">Hurun India / IndiQube</div><div class="pr-title">IndiQube Founders - Hurun India Top 200, 2025</div></div>
        <span class="pr-arrow">↗</span>
      </a>
      <a href="https://www.outlookbusiness.com/corporate/id-rather-be-known-for-building-well-than-building-as-a-woman-meghna-agarwal" target="_blank" class="pr-card">
        <span class="pr-num">05</span>
        <div class="pr-body"><div class="pr-source">Outlook Business</div><div class="pr-title">Meghna Agarwal - Leadership Interview</div></div>
        <span class="pr-arrow">↗</span>
      </a>
      <a href="https://www.businessworld.in/article/100-most-influential-women-2026-driving-india-s-700-bn-economic-opportunity-596723" target="_blank" class="pr-card">
        <span class="pr-num">06</span>
        <div class="pr-body"><div class="pr-source">Business World</div><div class="pr-title">100 Most Influential Women 2026 - IndiQube Founder</div></div>
        <span class="pr-arrow">↗</span>
      </a>
      <a href="https://www.exchange4media.com/pr-and-corporate-communication-news/international-womens-day-2026-women-leaders-on-why-giving-is-the-real-growth-enabler-152660.html" target="_blank" class="pr-card">
        <span class="pr-num">07</span>
        <div class="pr-body"><div class="pr-source">Exchange4Media</div><div class="pr-title">Women Leaders on Growth Enablers - IWD 2026</div></div>
        <span class="pr-arrow">↗</span>
      </a>
    </div>
    <p style="font-size:0.65rem;letter-spacing:0.2em;text-transform:uppercase;color:var(--warm);margin-bottom:1rem;">Video Collaborations &amp; Thought Leadership</p>
    <div class="cards-grid">
      <a href="https://www.youtube.com/watch?v=NzG-BNfvnhs" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/NzG-BNfvnhs/mqdefault.jpg" alt="IndiQube"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Video Collab</span><p class="card-title">IndiQube - Thought Leadership #1</p><span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=br0rRDmXCh8" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/br0rRDmXCh8/mqdefault.jpg" alt="IndiQube"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Video Collab</span><p class="card-title">IndiQube - Thought Leadership #2</p><span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=-qePS4fmles" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/-qePS4fmles/mqdefault.jpg" alt="IndiQube"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Video Collab</span><p class="card-title">IndiQube - Thought Leadership #3</p><span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=hJxGAKQDZ70" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/hJxGAKQDZ70/mqdefault.jpg" alt="IndiQube"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Video Collab</span><p class="card-title">IndiQube - Thought Leadership #4</p><span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=jIeQY_LVzOA" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/jIeQY_LVzOA/mqdefault.jpg" alt="IndiQube"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Video Collab</span><p class="card-title">IndiQube - Video Feature #5</p><span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=MzwzHuYoVi0" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/MzwzHuYoVi0/mqdefault.jpg" alt="IndiQube"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Video Collab</span><p class="card-title">IndiQube - Video Feature #6</p><span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=kNsxhdtVURw" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/kNsxhdtVURw/mqdefault.jpg" alt="IndiQube"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Video Collab</span><p class="card-title">IndiQube - Video Feature #7</p><span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=2nH4Ho6y4G0" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/2nH4Ho6y4G0/mqdefault.jpg" alt="IndiQube"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Video Collab</span><p class="card-title">IndiQube - Video Feature #8</p><span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=2u5dFYng950" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/2u5dFYng950/mqdefault.jpg" alt="IndiQube"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Video Collab</span><p class="card-title">IndiQube - Video Feature #9</p><span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=QtEiUcyr9IY" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/QtEiUcyr9IY/mqdefault.jpg" alt="IndiQube"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Video Collab</span><p class="card-title">IndiQube - Video Feature #10</p><span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=6165UxGT9A4" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/6165UxGT9A4/mqdefault.jpg" alt="IndiQube"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Video Collab</span><p class="card-title">IndiQube - Video Feature #11</p><span class="card-arrow">Watch →</span>
      </a>
      <a href="https://www.youtube.com/watch?v=hL1CY8ziXYo" target="_blank" class="work-card">
        <div class="yt-thumb"><img src="https://img.youtube.com/vi/hL1CY8ziXYo/mqdefault.jpg" alt="IndiQube"><div class="yt-play"><svg viewBox="0 0 10 12"><polygon points="0,0 10,6 0,12"/></svg></div></div>
        <span class="card-type">Video Collab</span><p class="card-title">IndiQube - Video Feature #12</p><span class="card-arrow">Watch →</span>
      </a>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="contact-inner">
    <p class="contact-eyebrow reveal">03 - Let's Talk</p>
    <h2 class="contact-heading reveal">Open to<br><em>new opportunities.</em></h2>
    <div class="contact-links reveal">
      <a href="mailto:siddharth.indy@gmail.com" class="contact-link">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
        Email Me
        
      </a>
      <a href="https://www.linkedin.com/in/sidharthapriyadarshi" target="_blank" class="contact-link">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>
        LinkedIn
        
      </a>
      <a href="https://drive.google.com/file/d/1-DZvzTGCOPr7VrsdTRLU0Y0wD8Z2F5on/view?usp=sharing" target="_blank" class="contact-link">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8z"/><polyline points="14 2 14 8 20 8"/></svg>
        Download CV
        
           </a>
    </div>
  </div>
</section>

<footer>
  <span>© 2026 Sidhartha Priyadarshi </span>
  <span>Global Indian</span>
  
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
  function animateCursor() {
    cursor.style.left = mx + 'px'; cursor.style.top = my + 'px';
    rx += (mx - rx) * 0.12; ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px'; ring.style.top = ry + 'px';
    requestAnimationFrame(animateCursor);
  }
  animateCursor();
  document.querySelectorAll('a, button').forEach(el => {
    el.addEventListener('mouseenter', () => { cursor.style.width = '18px'; cursor.style.height = '18px'; ring.style.width = '54px'; ring.style.height = '54px'; });
    el.addEventListener('mouseleave', () => { cursor.style.width = '10px'; cursor.style.height = '10px'; ring.style.width = '36px'; ring.style.height = '36px'; });
  });
  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); observer.unobserve(e.target); } });
  }, { threshold: 0.1 });
  reveals.forEach(el => observer.observe(el));
</script>
</body>
</html>
