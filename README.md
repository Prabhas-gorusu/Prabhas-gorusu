<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Prabhas Gorusu — Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&family=Syne:wght@400;600;800&display=swap" rel="stylesheet"/>
<style>
:root {
  --cyan: #00f5ff;
  --teal: #64ffda;
  --pink: #ff2d78;
  --dim: #0a0e1a;
  --mid: #0d1b2a;
  --card: rgba(0,245,255,0.04);
  --border: rgba(0,245,255,0.15);
}

*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }

html { scroll-behavior: smooth; }

body {
  background: var(--dim);
  color: #ccd6f6;
  font-family: 'Syne', sans-serif;
  overflow-x: hidden;
  cursor: none;
}

/* ═══════════════ CURSOR ═══════════════ */
#cursor {
  position: fixed; top:0; left:0; pointer-events:none; z-index:9999;
  width:12px; height:12px;
  background: var(--cyan);
  border-radius:50%;
  transform: translate(-50%,-50%);
  transition: transform .1s, width .2s, height .2s, opacity .2s;
  box-shadow: 0 0 10px var(--cyan), 0 0 30px rgba(0,245,255,.4);
  mix-blend-mode: screen;
}
#cursor-ring {
  position: fixed; top:0; left:0; pointer-events:none; z-index:9998;
  width:36px; height:36px;
  border:1.5px solid rgba(0,245,255,.5);
  border-radius:50%;
  transform: translate(-50%,-50%);
  transition: transform .15s ease-out, width .3s, height .3s;
}
body:hover #cursor { opacity:1; }

/* ═══════════════ CANVAS ═══════════════ */
#canvas {
  position: fixed; top:0; left:0;
  width:100%; height:100%;
  pointer-events:none; z-index:0;
  opacity:.55;
}

/* ═══════════════ SECTIONS ═══════════════ */
section { position:relative; z-index:1; }

/* ═══════════════ NAV ═══════════════ */
nav {
  position: fixed; top:0; width:100%; z-index:100;
  padding: 1.2rem 3rem;
  display: flex; justify-content:space-between; align-items:center;
  background: linear-gradient(to bottom, rgba(10,14,26,.95), transparent);
  backdrop-filter: blur(8px);
  border-bottom: 1px solid var(--border);
}
.nav-logo {
  font-family: 'Orbitron', monospace;
  font-size: 1.1rem; font-weight:900;
  color: var(--cyan);
  letter-spacing: .2em;
  text-shadow: 0 0 20px var(--cyan);
}
.nav-links { display:flex; gap:2rem; list-style:none; }
.nav-links a {
  font-family: 'Share Tech Mono', monospace;
  color: #8892b0; text-decoration:none;
  font-size: .85rem; letter-spacing:.1em;
  transition: color .3s;
  position: relative;
}
.nav-links a::after {
  content:''; position:absolute; bottom:-4px; left:0;
  width:0; height:1px; background:var(--cyan);
  transition: width .3s;
}
.nav-links a:hover { color:var(--cyan); }
.nav-links a:hover::after { width:100%; }

/* ═══════════════ HERO ═══════════════ */
#hero {
  min-height: 100vh;
  display: flex; align-items:center; justify-content:center;
  padding: 6rem 3rem 4rem;
  text-align: center;
}
.hero-inner { max-width:900px; }

.glitch-wrap {
  position:relative; display:inline-block;
  margin-bottom: 1.5rem;
}
.glitch-name {
  font-family: 'Orbitron', monospace;
  font-size: clamp(3rem,8vw,6rem);
  font-weight: 900;
  color: #fff;
  letter-spacing: .06em;
  text-shadow: 0 0 40px rgba(0,245,255,.5);
  position: relative;
  animation: glitch-skew 4s infinite linear alternate-reverse;
}
.glitch-name::before,
.glitch-name::after {
  content: attr(data-text);
  position:absolute; top:0; left:0; width:100%; height:100%;
}
.glitch-name::before {
  color: var(--pink);
  clip-path: polygon(0 0,100% 0,100% 35%,0 35%);
  animation: glitch-top 3.5s infinite linear;
  opacity: .85;
}
.glitch-name::after {
  color: var(--teal);
  clip-path: polygon(0 65%,100% 65%,100% 100%,0 100%);
  animation: glitch-bot 4s infinite linear;
  opacity: .85;
}
@keyframes glitch-top {
  0%,90% { transform:translate(0,0); opacity:0; }
  91%     { transform:translate(-3px,-1px); opacity:.85; }
  93%     { transform:translate(3px,1px); opacity:.85; }
  95%     { transform:translate(-2px,0); opacity:.85; }
  100%    { transform:translate(0,0); opacity:0; }
}
@keyframes glitch-bot {
  0%,85% { transform:translate(0,0); opacity:0; }
  86%    { transform:translate(3px,2px); opacity:.85; }
  88%    { transform:translate(-3px,-1px); opacity:.85; }
  90%    { transform:translate(0,0); opacity:0; }
}
@keyframes glitch-skew {
  0%  { transform:skewX(0deg); }
  98% { transform:skewX(0deg); }
  99% { transform:skewX(-1.5deg); }
  100%{ transform:skewX(0deg); }
}

.hero-subtitle {
  font-family: 'Share Tech Mono', monospace;
  font-size: clamp(.9rem,2vw,1.1rem);
  color: var(--teal);
  letter-spacing: .25em;
  margin-bottom: 2rem;
  opacity: 0;
  animation: fadeUp .8s .6s forwards;
}
.hero-desc {
  font-size:1.05rem; line-height:1.8;
  color:#8892b0; max-width:600px; margin:0 auto 2.5rem;
  opacity:0; animation: fadeUp .8s .9s forwards;
}

.hero-tags {
  display:flex; flex-wrap:wrap; gap:.7rem;
  justify-content:center; margin-bottom:3rem;
  opacity:0; animation: fadeUp .8s 1.1s forwards;
}
.tag {
  font-family:'Share Tech Mono',monospace;
  font-size:.75rem; letter-spacing:.1em;
  padding:.4rem .9rem;
  border:1px solid var(--border);
  border-radius:3px;
  background: var(--card);
  color: var(--teal);
  transition: border-color .3s, box-shadow .3s, transform .2s;
}
.tag:hover {
  border-color: var(--cyan);
  box-shadow: 0 0 12px rgba(0,245,255,.3);
  transform:translateY(-2px);
}

.hero-cta {
  display:flex; gap:1.2rem; justify-content:center;
  opacity:0; animation:fadeUp .8s 1.3s forwards;
}
.btn {
  font-family:'Orbitron',monospace; font-size:.75rem; font-weight:700;
  letter-spacing:.15em; padding:.85rem 2rem;
  border-radius:3px; text-decoration:none;
  transition: all .3s; cursor:none;
}
.btn-primary {
  background: transparent;
  border:1.5px solid var(--cyan);
  color: var(--cyan);
  box-shadow: inset 0 0 0 0 var(--cyan);
  transition: box-shadow .3s, color .3s;
}
.btn-primary:hover {
  box-shadow: inset 0 0 0 40px rgba(0,245,255,.12);
  text-shadow: 0 0 8px var(--cyan);
}
.btn-secondary {
  background: transparent;
  border:1.5px solid rgba(100,255,218,.4);
  color: #8892b0;
}
.btn-secondary:hover { border-color:var(--teal); color:var(--teal); }

.scroll-indicator {
  position:absolute; bottom:2.5rem; left:50%;
  transform:translateX(-50%);
  display:flex; flex-direction:column; align-items:center; gap:.5rem;
  opacity:0; animation:fadeIn 1s 2s forwards;
}
.scroll-line {
  width:1px; height:60px;
  background: linear-gradient(to bottom, var(--cyan), transparent);
  animation: scrollDrop 2s 2.2s infinite;
}
.scroll-text {
  font-family:'Share Tech Mono',monospace;
  font-size:.65rem; letter-spacing:.2em; color:#8892b0;
  writing-mode:vertical-rl; text-orientation:mixed;
}
@keyframes scrollDrop {
  0%   { transform:scaleY(0); transform-origin:top; }
  50%  { transform:scaleY(1); transform-origin:top; }
  51%  { transform:scaleY(1); transform-origin:bottom; }
  100% { transform:scaleY(0); transform-origin:bottom; }
}

/* ═══════════════ SECTION TITLES ═══════════════ */
.section-header {
  text-align:center; margin-bottom:4rem;
  opacity:0; transform:translateY(30px);
  transition: opacity .8s, transform .8s;
}
.section-header.visible { opacity:1; transform:translateY(0); }

.section-label {
  font-family:'Share Tech Mono',monospace;
  font-size:.75rem; letter-spacing:.3em;
  color:var(--cyan); margin-bottom:.8rem;
  display:block;
}
.section-title {
  font-family:'Orbitron',monospace;
  font-size:clamp(1.6rem,4vw,2.4rem);
  font-weight:900; color:#ccd6f6;
  letter-spacing:.05em;
}
.section-line {
  width:80px; height:2px;
  background: linear-gradient(to right, var(--cyan), var(--teal));
  margin:1.2rem auto 0;
  box-shadow: 0 0 10px var(--cyan);
}

/* ═══════════════ ABOUT ═══════════════ */
#about { padding:7rem 3rem; }
.about-grid {
  max-width:1100px; margin:0 auto;
  display:grid; grid-template-columns:1fr 1fr; gap:5rem;
  align-items:center;
}
.about-visual {
  position:relative; display:flex;
  justify-content:center; align-items:center;
  opacity:0; transform:translateX(-40px);
  transition: opacity .8s .2s, transform .8s .2s;
}
.about-visual.visible { opacity:1; transform:translateX(0); }

.avatar-orbit {
  position:relative; width:280px; height:280px;
}
.orbit-ring {
  position:absolute; border-radius:50%;
  border:1px solid;
  animation: spinOrbit linear infinite;
  top:50%; left:50%; transform:translate(-50%,-50%);
}
.orbit-1 { width:280px;height:280px; border-color:rgba(0,245,255,.2); animation-duration:20s; }
.orbit-2 { width:220px;height:220px; border-color:rgba(100,255,218,.15); animation-duration:15s; animation-direction:reverse; }
.orbit-3 { width:160px;height:160px; border-color:rgba(255,45,120,.1); animation-duration:10s; }

.orbit-dot {
  position:absolute; width:8px;height:8px;
  border-radius:50%;
  top:0; left:50%; transform:translate(-50%,-50%);
}
.dot-cyan  { background:var(--cyan); box-shadow:0 0 8px var(--cyan); }
.dot-teal  { background:var(--teal); box-shadow:0 0 8px var(--teal); }
.dot-pink  { background:var(--pink); box-shadow:0 0 8px var(--pink); }

.avatar-core {
  position:absolute; top:50%; left:50%;
  transform:translate(-50%,-50%);
  width:120px; height:120px;
  border-radius:50%;
  background: linear-gradient(135deg, rgba(0,245,255,.15), rgba(100,255,218,.08));
  border:2px solid rgba(0,245,255,.4);
  display:flex; align-items:center; justify-content:center;
  font-family:'Orbitron',monospace;
  font-size:2.8rem; font-weight:900;
  color:var(--cyan);
  box-shadow: 0 0 30px rgba(0,245,255,.2), inset 0 0 30px rgba(0,245,255,.05);
  animation: avatarPulse 3s ease-in-out infinite;
}
@keyframes avatarPulse {
  0%,100% { box-shadow:0 0 30px rgba(0,245,255,.2),inset 0 0 30px rgba(0,245,255,.05); }
  50%     { box-shadow:0 0 50px rgba(0,245,255,.4),inset 0 0 40px rgba(0,245,255,.1); }
}
@keyframes spinOrbit { to { transform:translate(-50%,-50%) rotate(360deg); } }

.about-text {
  opacity:0; transform:translateX(40px);
  transition: opacity .8s .3s, transform .8s .3s;
}
.about-text.visible { opacity:1; transform:translateX(0); }

.about-text h3 {
  font-family:'Orbitron',monospace; font-size:1.4rem;
  color:#fff; margin-bottom:1.2rem;
  letter-spacing:.05em;
}
.about-text p {
  color:#8892b0; line-height:1.9; margin-bottom:1.2rem;
  font-size:.95rem;
}
.about-text p span { color:var(--teal); font-weight:600; }

.stat-row {
  display:grid; grid-template-columns:repeat(3,1fr);
  gap:1rem; margin-top:2rem;
}
.stat-box {
  background:var(--card); border:1px solid var(--border);
  border-radius:6px; padding:1rem;
  text-align:center;
  transition:border-color .3s, transform .3s;
}
.stat-box:hover { border-color:var(--cyan); transform:translateY(-3px); }
.stat-num {
  font-family:'Orbitron',monospace;
  font-size:1.6rem; font-weight:900;
  color:var(--cyan);
  text-shadow:0 0 15px var(--cyan);
}
.stat-label {
  font-family:'Share Tech Mono',monospace;
  font-size:.65rem; letter-spacing:.1em; color:#8892b0;
  margin-top:.3rem;
}

/* ═══════════════ SKILLS ═══════════════ */
#skills { padding:7rem 3rem; background: linear-gradient(180deg, transparent, rgba(0,245,255,.02), transparent); }
.skills-grid {
  max-width:1100px; margin:0 auto;
  display:grid; grid-template-columns:repeat(auto-fit,minmax(300px,1fr)); gap:2rem;
}
.skill-category {
  background:var(--card); border:1px solid var(--border);
  border-radius:8px; padding:2rem;
  opacity:0; transform:translateY(30px);
  transition: opacity .7s, transform .7s, border-color .3s;
}
.skill-category.visible { opacity:1; transform:translateY(0); }
.skill-category:hover { border-color:rgba(0,245,255,.35); }

.cat-title {
  font-family:'Orbitron',monospace; font-size:.85rem;
  color:var(--cyan); letter-spacing:.15em;
  margin-bottom:1.5rem;
  display:flex; align-items:center; gap:.7rem;
}
.cat-icon { font-size:1.1rem; }

.skill-item { margin-bottom:1.2rem; }
.skill-meta {
  display:flex; justify-content:space-between;
  font-family:'Share Tech Mono',monospace;
  font-size:.75rem; color:#8892b0; margin-bottom:.5rem;
}
.skill-pct { color:var(--teal); }
.skill-bar-bg {
  height:4px; background:rgba(255,255,255,.07);
  border-radius:2px; overflow:hidden;
}
.skill-bar-fill {
  height:100%; width:0; border-radius:2px;
  background: linear-gradient(to right, var(--cyan), var(--teal));
  box-shadow:0 0 8px var(--cyan);
  transition: width 1.2s cubic-bezier(.4,0,.2,1);
}

/* ═══════════════ PROJECTS ═══════════════ */
#projects { padding:7rem 3rem; }
.projects-grid {
  max-width:1100px; margin:0 auto;
  display:grid; grid-template-columns:repeat(auto-fit,minmax(340px,1fr)); gap:2rem;
}
.project-card {
  position:relative; overflow:hidden;
  background:var(--card); border:1px solid var(--border);
  border-radius:10px; padding:2rem;
  opacity:0; transform:translateY(40px);
  transition: opacity .7s, transform .7s, border-color .3s, box-shadow .3s;
  cursor:none;
}
.project-card.visible { opacity:1; transform:translateY(0); }
.project-card:hover {
  border-color:rgba(0,245,255,.5);
  box-shadow:0 0 40px rgba(0,245,255,.08), 0 0 1px var(--cyan);
  transform:translateY(-6px);
}
.project-card::before {
  content:'';
  position:absolute; top:0; left:-100%;
  width:60%; height:100%;
  background:linear-gradient(90deg,transparent,rgba(0,245,255,.04),transparent);
  transition:left .6s;
}
.project-card:hover::before { left:150%; }

.proj-number {
  font-family:'Orbitron',monospace;
  font-size:.7rem; color:rgba(0,245,255,.4);
  letter-spacing:.3em; margin-bottom:1.2rem;
}
.proj-icon { font-size:2.4rem; margin-bottom:1rem; }
.proj-title {
  font-family:'Orbitron',monospace;
  font-size:1.15rem; font-weight:700;
  color:#ccd6f6; margin-bottom:.8rem;
  letter-spacing:.05em;
}
.proj-desc {
  color:#8892b0; font-size:.88rem;
  line-height:1.75; margin-bottom:1.5rem;
}
.proj-tech {
  display:flex; flex-wrap:wrap; gap:.5rem; margin-bottom:1.5rem;
}
.tech-pill {
  font-family:'Share Tech Mono',monospace;
  font-size:.7rem; padding:.3rem .7rem;
  border:1px solid rgba(0,245,255,.2);
  border-radius:3px; color:var(--teal);
  background:rgba(0,245,255,.04);
}
.proj-link {
  font-family:'Share Tech Mono',monospace;
  font-size:.75rem; letter-spacing:.12em;
  color:var(--cyan); text-decoration:none;
  display:flex; align-items:center; gap:.5rem;
  transition:gap .3s;
}
.proj-link:hover { gap:.9rem; }
.proj-metric {
  position:absolute; top:1.5rem; right:1.5rem;
  font-family:'Orbitron',monospace;
  font-size:.7rem; color:var(--pink);
  background:rgba(255,45,120,.08);
  border:1px solid rgba(255,45,120,.2);
  padding:.3rem .7rem; border-radius:20px;
}

/* ═══════════════ ACHIEVEMENTS ═══════════════ */
#achievements { padding:7rem 3rem; background:linear-gradient(180deg,transparent,rgba(100,255,218,.01),transparent); }
.ach-grid {
  max-width:1100px; margin:0 auto;
  display:grid; grid-template-columns:repeat(auto-fit,minmax(220px,1fr)); gap:1.5rem;
}
.ach-card {
  background:var(--card); border:1px solid var(--border);
  border-radius:8px; padding:1.8rem;
  text-align:center;
  opacity:0; transform:scale(.9);
  transition:opacity .6s, transform .6s, border-color .3s;
}
.ach-card.visible { opacity:1; transform:scale(1); }
.ach-card:hover { border-color:rgba(100,255,218,.4); }
.ach-emoji { font-size:2.2rem; margin-bottom:.8rem; }
.ach-title {
  font-family:'Orbitron',monospace;
  font-size:.8rem; color:#ccd6f6;
  letter-spacing:.08em; margin-bottom:.5rem;
}
.ach-desc { font-size:.8rem; color:#8892b0; line-height:1.6; }
.ach-rarity {
  display:inline-block; margin-top:.8rem;
  font-family:'Share Tech Mono',monospace;
  font-size:.65rem; letter-spacing:.1em;
  padding:.25rem .6rem; border-radius:3px;
}
.legendary { color:#ffd700; background:rgba(255,215,0,.08); border:1px solid rgba(255,215,0,.2); }
.epic      { color:#c678dd; background:rgba(198,120,221,.08); border:1px solid rgba(198,120,221,.2); }
.rare      { color:var(--cyan); background:rgba(0,245,255,.06); border:1px solid rgba(0,245,255,.2); }
.mythic    { color:var(--pink); background:rgba(255,45,120,.08); border:1px solid rgba(255,45,120,.2); }

/* ═══════════════ CONTACT ═══════════════ */
#contact { padding:7rem 3rem 5rem; }
.contact-inner {
  max-width:700px; margin:0 auto; text-align:center;
  opacity:0; transform:translateY(30px);
  transition:opacity .8s, transform .8s;
}
.contact-inner.visible { opacity:1; transform:translateY(0); }
.contact-tagline {
  font-size:1.1rem; color:#8892b0;
  line-height:1.8; margin-bottom:3rem;
}
.contact-tagline span { color:var(--teal); }
.contact-links {
  display:flex; flex-wrap:wrap; gap:1rem;
  justify-content:center; margin-bottom:3rem;
}
.contact-btn {
  font-family:'Orbitron',monospace; font-size:.7rem;
  letter-spacing:.15em; padding:.9rem 2rem;
  border-radius:4px; text-decoration:none;
  display:flex; align-items:center; gap:.6rem;
  transition:all .3s; cursor:none;
  border:1.5px solid var(--border);
  color:#8892b0; background:var(--card);
}
.contact-btn:hover {
  border-color:var(--cyan); color:var(--cyan);
  box-shadow:0 0 20px rgba(0,245,255,.15);
  transform:translateY(-3px);
}
.cb-icon { font-size:1rem; }

/* ═══════════════ FOOTER ═══════════════ */
footer {
  border-top:1px solid var(--border);
  padding:2rem 3rem;
  text-align:center;
  font-family:'Share Tech Mono',monospace;
  font-size:.75rem; letter-spacing:.1em; color:#4a5568;
  position:relative; z-index:1;
}
footer span { color:var(--teal); }

/* ═══════════════ KEYFRAMES ═══════════════ */
@keyframes fadeUp { from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)} }
@keyframes fadeIn { from{opacity:0}to{opacity:1} }

/* ═══════════════ SCANLINE ═══════════════ */
body::after {
  content:'';
  position:fixed; top:0; left:0; width:100%; height:100%;
  pointer-events:none; z-index:200;
  background:repeating-linear-gradient(0deg,rgba(0,0,0,.03) 0,rgba(0,0,0,.03) 1px,transparent 1px,transparent 3px);
}

/* ═══════════════ RESPONSIVE ═══════════════ */
@media(max-width:768px){
  nav{padding:1rem 1.5rem;}
  .nav-links{display:none;}
  .about-grid{grid-template-columns:1fr; gap:3rem;}
  .about-visual{order:0;}
  .about-text{order:1;}
  #hero,#about,#skills,#projects,#achievements,#contact{padding:5rem 1.5rem;}
}
</style>
</head>
<body>

<!-- Custom cursor -->
<div id="cursor"></div>
<div id="cursor-ring"></div>

<!-- Neural particle canvas -->
<canvas id="canvas"></canvas>

<!-- Navigation -->
<nav>
  <div class="nav-logo">PG://</div>
  <ul class="nav-links">
    <li><a href="#about">ABOUT</a></li>
    <li><a href="#skills">SKILLS</a></li>
    <li><a href="#projects">PROJECTS</a></li>
    <li><a href="#achievements">LOG</a></li>
    <li><a href="#contact">CONTACT</a></li>
  </ul>
</nav>

<!-- ═══ HERO ═══ -->
<section id="hero">
  <div class="hero-inner">
    <div class="glitch-wrap">
      <h1 class="glitch-name" data-text="PRABHAS GORUSU">PRABHAS GORUSU</h1>
    </div>
    <p class="hero-subtitle">FULL STACK DEVELOPER · AI ARCHITECT · CLOUD EXPLORER</p>
    <p class="hero-desc">
      Transforming caffeine and curiosity into code that lives in production.
      Based in Kakinada, India — building software that matters, one commit at a time.
    </p>
    <div class="hero-tags">
      <span class="tag">Python</span>
      <span class="tag">React</span>
      <span class="tag">Node.js</span>
      <span class="tag">Flutter</span>
      <span class="tag">TensorFlow</span>
      <span class="tag">AWS</span>
      <span class="tag">Docker</span>
      <span class="tag">FastAPI</span>
    </div>
    <div class="hero-cta">
      <a href="#projects" class="btn btn-primary">VIEW WORK</a>
      <a href="#contact" class="btn btn-secondary">GET IN TOUCH</a>
    </div>
  </div>
  <div class="scroll-indicator">
    <span class="scroll-text">SCROLL</span>
    <div class="scroll-line"></div>
  </div>
</section>

<!-- ═══ ABOUT ═══ -->
<section id="about">
  <div class="section-header">
    <span class="section-label">// 001 — IDENTITY</span>
    <h2 class="section-title">WHO IS PRABHAS?</h2>
    <div class="section-line"></div>
  </div>
  <div class="about-grid">
    <div class="about-visual">
      <div class="avatar-orbit">
        <div class="orbit-ring orbit-1"><div class="orbit-dot dot-cyan"></div></div>
        <div class="orbit-ring orbit-2"><div class="orbit-dot dot-teal"></div></div>
        <div class="orbit-ring orbit-3"><div class="orbit-dot dot-pink"></div></div>
        <div class="avatar-core">PG</div>
      </div>
    </div>
    <div class="about-text">
      <h3>Developer by Craft. Dreamer by Nature.</h3>
      <p>I'm a <span>Full Stack Developer</span> with a passion for building things that don't just work — they <span>feel right</span>. Whether it's a sleek UI or a backend service handling thousands of requests, I care about every layer.</p>
      <p>When I'm not pushing commits, I'm exploring <span>Cloud Architecture</span> and <span>System Design</span>, hunting for the next elegant solution to an inelegant problem.</p>
      <p>Fun fact: I can solve a <span>Rubik's Cube in under 2 minutes</span>. I approach code the same way — methodical, fast, satisfying.</p>
      <div class="stat-row">
        <div class="stat-box">
          <div class="stat-num" data-target="50">0</div>
          <div class="stat-label">K+ DOWNLOADS</div>
        </div>
        <div class="stat-box">
          <div class="stat-num" data-target="90">0</div>
          <div class="stat-label">% AI ACCURACY</div>
        </div>
        <div class="stat-box">
          <div class="stat-num" data-target="2">0</div>
          <div class="stat-label">MIN CUBE SOLVE</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ═══ SKILLS ═══ -->
<section id="skills">
  <div class="section-header">
    <span class="section-label">// 002 — ARSENAL</span>
    <h2 class="section-title">TECH STACK</h2>
    <div class="section-line"></div>
  </div>
  <div class="skills-grid">
    <div class="skill-category">
      <div class="cat-title"><span class="cat-icon">⌨️</span> LANGUAGES</div>
      <div class="skill-item"><div class="skill-meta"><span>Python</span><span class="skill-pct">95%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="95"></div></div></div>
      <div class="skill-item"><div class="skill-meta"><span>JavaScript</span><span class="skill-pct">90%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="90"></div></div></div>
      <div class="skill-item"><div class="skill-meta"><span>TypeScript</span><span class="skill-pct">80%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="80"></div></div></div>
      <div class="skill-item"><div class="skill-meta"><span>Dart</span><span class="skill-pct">85%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="85"></div></div></div>
    </div>
    <div class="skill-category">
      <div class="cat-title"><span class="cat-icon">⚡</span> FRAMEWORKS</div>
      <div class="skill-item"><div class="skill-meta"><span>React</span><span class="skill-pct">90%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="90"></div></div></div>
      <div class="skill-item"><div class="skill-meta"><span>Node.js</span><span class="skill-pct">88%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="88"></div></div></div>
      <div class="skill-item"><div class="skill-meta"><span>FastAPI</span><span class="skill-pct">85%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="85"></div></div></div>
      <div class="skill-item"><div class="skill-meta"><span>Flutter</span><span class="skill-pct">82%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="82"></div></div></div>
    </div>
    <div class="skill-category">
      <div class="cat-title"><span class="cat-icon">🤖</span> AI / ML</div>
      <div class="skill-item"><div class="skill-meta"><span>TensorFlow</span><span class="skill-pct">85%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="85"></div></div></div>
      <div class="skill-item"><div class="skill-meta"><span>PyTorch</span><span class="skill-pct">78%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="78"></div></div></div>
      <div class="skill-item"><div class="skill-meta"><span>OpenCV</span><span class="skill-pct">75%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="75"></div></div></div>
      <div class="skill-item"><div class="skill-meta"><span>Scikit-Learn</span><span class="skill-pct">80%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="80"></div></div></div>
    </div>
    <div class="skill-category">
      <div class="cat-title"><span class="cat-icon">☁️</span> CLOUD / DEVOPS</div>
      <div class="skill-item"><div class="skill-meta"><span>AWS</span><span class="skill-pct">80%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="80"></div></div></div>
      <div class="skill-item"><div class="skill-meta"><span>Google Cloud</span><span class="skill-pct">75%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="75"></div></div></div>
      <div class="skill-item"><div class="skill-meta"><span>Docker</span><span class="skill-pct">82%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="82"></div></div></div>
      <div class="skill-item"><div class="skill-meta"><span>Firebase</span><span class="skill-pct">88%</span></div><div class="skill-bar-bg"><div class="skill-bar-fill" data-width="88"></div></div></div>
    </div>
  </div>
</section>

<!-- ═══ PROJECTS ═══ -->
<section id="projects">
  <div class="section-header">
    <span class="section-label">// 003 — MISSIONS</span>
    <h2 class="section-title">FEATURED WORK</h2>
    <div class="section-line"></div>
  </div>
  <div class="projects-grid">
    <div class="project-card">
      <div class="proj-number">MISSION // 001</div>
      <div class="proj-metric">90% ACC</div>
      <div class="proj-icon">🤖</div>
      <h3 class="proj-title">Neural Chatbot</h3>
      <p class="proj-desc">An intelligent conversational AI that achieves 90% accuracy. Built with a transformer architecture, it handles complex context and delivers human-like responses at scale.</p>
      <div class="proj-tech">
        <span class="tech-pill">Python</span>
        <span class="tech-pill">TensorFlow</span>
        <span class="tech-pill">FastAPI</span>
        <span class="tech-pill">Redis</span>
      </div>
      <a class="proj-link" href="https://github.com/prabhas-gorusu/ai-chatbot" target="_blank">
        VIEW PROJECT →
      </a>
    </div>
    <div class="project-card">
      <div class="proj-number">MISSION // 002</div>
      <div class="proj-metric">50K+ DL</div>
      <div class="proj-icon">💪</div>
      <h3 class="proj-title">Fitness Tracker</h3>
      <p class="proj-desc">A cross-platform mobile app with 50,000+ downloads. Tracks workouts, nutrition, and progress with real-time sync across devices using Firebase.</p>
      <div class="proj-tech">
        <span class="tech-pill">Flutter</span>
        <span class="tech-pill">Firebase</span>
        <span class="tech-pill">Dart</span>
        <span class="tech-pill">ML Kit</span>
      </div>
      <a class="proj-link" href="https://github.com/prabhas-gorusu/fitness-app" target="_blank">
        VIEW PROJECT →
      </a>
    </div>
    <div class="project-card">
      <div class="proj-number">MISSION // 003</div>
      <div class="proj-metric">WIP</div>
      <div class="proj-icon">🚀</div>
      <h3 class="proj-title">Next Mission</h3>
      <p class="proj-desc">Something big is brewing. Always building, always exploring. Follow the GitHub to catch the next drop before anyone else does.</p>
      <div class="proj-tech">
        <span class="tech-pill">???</span>
        <span class="tech-pill">Stay Tuned</span>
      </div>
      <a class="proj-link" href="https://github.com/prabhas-gorusu" target="_blank">
        WATCH REPO →
      </a>
    </div>
  </div>
</section>

<!-- ═══ ACHIEVEMENTS ═══ -->
<section id="achievements">
  <div class="section-header">
    <span class="section-label">// 004 — ACHIEVEMENT LOG</span>
    <h2 class="section-title">UNLOCKED</h2>
    <div class="section-line"></div>
  </div>
  <div class="ach-grid">
    <div class="ach-card">
      <div class="ach-emoji">🏆</div>
      <div class="ach-title">Speed Cuber</div>
      <div class="ach-desc">Solved Rubik's Cube in under 2 minutes. Applies same approach to bugs.</div>
      <span class="ach-rarity legendary">LEGENDARY</span>
    </div>
    <div class="ach-card">
      <div class="ach-emoji">🤖</div>
      <div class="ach-title">AI Whisperer</div>
      <div class="ach-desc">Built a chatbot that achieves 90% accuracy in production.</div>
      <span class="ach-rarity epic">EPIC</span>
    </div>
    <div class="ach-card">
      <div class="ach-emoji">📱</div>
      <div class="ach-title">Mass Adoption</div>
      <div class="ach-desc">Shipped a Flutter app to 50,000+ real users worldwide.</div>
      <span class="ach-rarity rare">RARE</span>
    </div>
    <div class="ach-card">
      <div class="ach-emoji">☁️</div>
      <div class="ach-title">Cloud Walker</div>
      <div class="ach-desc">Deployed to AWS, GCP, and Firebase without a single breakdown.</div>
      <span class="ach-rarity rare">RARE</span>
    </div>
    <div class="ach-card">
      <div class="ach-emoji">🐛</div>
      <div class="ach-title">3AM Debugger</div>
      <div class="ach-desc">Fixed a critical bug at 3AM and actually understood why it worked.</div>
      <span class="ach-rarity mythic">MYTHIC</span>
    </div>
    <div class="ach-card">
      <div class="ach-emoji">☕</div>
      <div class="ach-title">Caffeine Powered</div>
      <div class="ach-desc">Survived multiple hackathons on coffee alone. No casualties.</div>
      <span class="ach-rarity legendary">LEGENDARY</span>
    </div>
  </div>
</section>

<!-- ═══ CONTACT ═══ -->
<section id="contact">
  <div class="section-header">
    <span class="section-label">// 005 — TRANSMISSION</span>
    <h2 class="section-title">LET'S BUILD TOGETHER</h2>
    <div class="section-line"></div>
  </div>
  <div class="contact-inner">
    <p class="contact-tagline">
      Got a <span>wild idea</span>? A startup in your head? An open-source project that needs a co-conspirator?
      A bug that's haunted you for days?<br/><br/>
      My inbox is open. I <span>don't ghost</span>.
    </p>
    <div class="contact-links">
      <a class="contact-btn" href="mailto:prabhasgorusu001@gmail.com"><span class="cb-icon">✉️</span> EMAIL</a>
      <a class="contact-btn" href="https://linkedin.com/in/prabhas-gorusu" target="_blank"><span class="cb-icon">🔗</span> LINKEDIN</a>
      <a class="contact-btn" href="https://github.com/prabhas-gorusu" target="_blank"><span class="cb-icon">⌥</span> GITHUB</a>
      <a class="contact-btn" href="https://x.com/prabhas__gorusu" target="_blank"><span class="cb-icon">✕</span> TWITTER</a>
    </div>
  </div>
</section>

<footer>
  BUILT WITH <span>&lt;/SOUL&gt;</span> BY <span>PRABHAS GORUSU</span> · KAKINADA, INDIA · 2025
</footer>

<!-- ═══════════════ JAVASCRIPT ═══════════════ -->
<script>
// ─── Custom Cursor ───────────────────────────────────────────────
const cursor = document.getElementById('cursor');
const ring   = document.getElementById('cursor-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{
  mx=e.clientX; my=e.clientY;
  cursor.style.left=mx+'px'; cursor.style.top=my+'px';
});
function animateRing(){
  rx+=(mx-rx)*.12; ry+=(my-ry)*.12;
  ring.style.left=rx+'px'; ring.style.top=ry+'px';
  requestAnimationFrame(animateRing);
}
animateRing();
document.querySelectorAll('a,button').forEach(el=>{
  el.addEventListener('mouseenter',()=>{
    cursor.style.width='20px';cursor.style.height='20px';
    ring.style.width='56px';ring.style.height='56px';
  });
  el.addEventListener('mouseleave',()=>{
    cursor.style.width='12px';cursor.style.height='12px';
    ring.style.width='36px';ring.style.height='36px';
  });
});

// ─── Neural Particle Canvas ────────────────────────────────────────
const canvas=document.getElementById('canvas');
const ctx=canvas.getContext('2d');
let W,H,particles=[];

function resize(){
  W=canvas.width=window.innerWidth;
  H=canvas.height=window.innerHeight;
}
resize(); window.addEventListener('resize',resize);

class Particle {
  constructor(){
    this.reset();
    this.y=Math.random()*H;
  }
  reset(){
    this.x=Math.random()*W;
    this.y=Math.random()*H;
    this.r=Math.random()*1.5+.5;
    this.vx=(Math.random()-.5)*.4;
    this.vy=(Math.random()-.5)*.4;
    this.alpha=Math.random()*.7+.3;
    this.hue=Math.random()<.7?'0,245,255':'100,255,218';
  }
  update(){
    this.x+=this.vx; this.y+=this.vy;
    if(this.x<0||this.x>W||this.y<0||this.y>H) this.reset();
  }
  draw(){
    ctx.beginPath();
    ctx.arc(this.x,this.y,this.r,0,Math.PI*2);
    ctx.fillStyle=`rgba(${this.hue},${this.alpha})`;
    ctx.fill();
  }
}

const COUNT=Math.min(120,Math.floor(W*H/8000));
for(let i=0;i<COUNT;i++) particles.push(new Particle());

function drawLines(){
  for(let i=0;i<particles.length;i++){
    for(let j=i+1;j<particles.length;j++){
      const dx=particles[i].x-particles[j].x;
      const dy=particles[i].y-particles[j].y;
      const dist=Math.sqrt(dx*dx+dy*dy);
      if(dist<130){
        ctx.beginPath();
        ctx.moveTo(particles[i].x,particles[i].y);
        ctx.lineTo(particles[j].x,particles[j].y);
        const a=(1-dist/130)*.15;
        ctx.strokeStyle=`rgba(0,245,255,${a})`;
        ctx.lineWidth=.6;
        ctx.stroke();
      }
    }
  }
}

function animateCanvas(){
  ctx.clearRect(0,0,W,H);
  particles.forEach(p=>{p.update();p.draw();});
  drawLines();
  requestAnimationFrame(animateCanvas);
}
animateCanvas();

// ─── Scroll Reveal ─────────────────────────────────────────────────
const revealEls=document.querySelectorAll('.section-header,.about-visual,.about-text,.skill-category,.project-card,.ach-card,.contact-inner');
const io=new IntersectionObserver(entries=>{
  entries.forEach((e,i)=>{
    if(e.isIntersecting){
      // stagger siblings
      const siblings=[...e.target.parentElement.querySelectorAll(':scope > .skill-category,:scope > .project-card,:scope > .ach-card')];
      const idx=siblings.indexOf(e.target);
      e.target.style.transitionDelay=(idx>=0?(idx*.12)+'s':'0s');
      e.target.classList.add('visible');
    }
  });
},{threshold:.15});
revealEls.forEach(el=>io.observe(el));

// ─── Animated Counters ─────────────────────────────────────────────
const statNums=document.querySelectorAll('.stat-num[data-target]');
const sio=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      const el=e.target;
      const target=+el.dataset.target;
      let current=0;
      const step=target/60;
      const t=setInterval(()=>{
        current+=step;
        if(current>=target){current=target;clearInterval(t);}
        el.textContent=Math.floor(current);
      },20);
      sio.unobserve(el);
    }
  });
},{threshold:.5});
statNums.forEach(el=>sio.observe(el));

// ─── Skill Bar Fills ───────────────────────────────────────────────
const bars=document.querySelectorAll('.skill-bar-fill');
const bio=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.style.width=e.target.dataset.width+'%';
      bio.unobserve(e.target);
    }
  });
},{threshold:.4});
bars.forEach(b=>bio.observe(b));

// ─── Smooth nav scroll ─────────────────────────────────────────────
document.querySelectorAll('a[href^="#"]').forEach(a=>{
  a.addEventListener('click',e=>{
    e.preventDefault();
    const t=document.querySelector(a.getAttribute('href'));
    if(t) t.scrollIntoView({behavior:'smooth',block:'start'});
  });
});
</script>
</body>
</html>
