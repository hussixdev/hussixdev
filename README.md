
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#030712">
<title>HUSSI DEV — ARCTIC OS</title>
<style>
:root {
  --bg: #030712;
  --panel: rgba(15, 23, 42, .72);
  --ice: #bae6fd;
  --white: #f8fafc;
  --muted: #94a3b8;
  --line: rgba(186, 230, 253, .22);
}
* { box-sizing: border-box; }
html { scroll-behavior: smooth; }
body {
  margin: 0;
  color: var(--white);
  background:
    radial-gradient(ellipse at 15% 10%, #102b42 0, transparent 36%),
    radial-gradient(ellipse at 85% 40%, #102034 0, transparent 35%),
    var(--bg);
  font-family: Inter, ui-sans-serif, system-ui, sans-serif;
  overflow-x: hidden;
}
a { color: inherit; text-decoration: none; }
button, a { -webkit-tap-highlight-color: transparent; }
::selection { background: var(--ice); color: #030712; }

#snow {
  position: fixed;
  inset: 0;
  z-index: 5;
  width: 100%;
  height: 100%;
  pointer-events: none;
}
.noise {
  position: fixed;
  inset: 0;
  z-index: 4;
  pointer-events: none;
  opacity: .13;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 180 180' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='.14'/%3E%3C/svg%3E");
}
.aurora {
  position: fixed;
  z-index: -1;
  width: 80vw;
  height: 45vw;
  top: -20vw;
  left: 10vw;
  background: #38bdf8;
  filter: blur(150px);
  opacity: .08;
  border-radius: 50%;
  animation: aurora 14s ease-in-out infinite alternate;
}
@keyframes aurora {
  from { transform: translate(-10%, 0) rotate(-10deg); opacity: .04; }
  to { transform: translate(10%, 35%) rotate(15deg); opacity: .13; }
}
@keyframes float {
  0%,100% { transform: translateY(0); }
  50% { transform: translateY(-12px); }
}
@keyframes glow {
  0%,100% { box-shadow: 0 0 15px #38bdf815; }
  50% { box-shadow: 0 0 35px #38bdf835; }
}
@keyframes rotate {
  to { transform: rotate(360deg); }
}
@keyframes shine {
  from { background-position: -200% 0; }
  to { background-position: 200% 0; }
}
@keyframes enter {
  from { opacity: 0; transform: translateY(24px); }
  to { opacity: 1; transform: translateY(0); }
}
.wrap { width: min(1120px, 90%); margin: auto; }
nav {
  position: sticky;
  top: 12px;
  z-index: 20;
  width: min(1120px, 94%);
  margin: 12px auto 0;
  padding: 13px 18px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  border: 1px solid var(--line);
  border-radius: 18px;
  background: #030712c9;
  backdrop-filter: blur(22px);
}
.logo {
  font-size: 16px;
  font-weight: 950;
  letter-spacing: 2px;
}
.logo span { color: var(--ice); }
.navlinks { display: flex; gap: 22px; color: var(--muted); font-size: 12px; }
.navlinks a:hover { color: var(--ice); }
.status {
  font: 10px ui-monospace, monospace;
  color: var(--ice);
  white-space: nowrap;
}
.status::before {
  content: "";
  display: inline-block;
  width: 7px; height: 7px;
  border-radius: 50%;
  margin-right: 7px;
  background: #a7f3d0;
  box-shadow: 0 0 12px #a7f3d0;
}
.hero {
  min-height: 680px;
  display: grid;
  place-items: center;
  text-align: center;
  position: relative;
  padding: 100px 0 80px;
}
.orbit {
  position: absolute;
  width: min(75vw, 520px);
  aspect-ratio: 1;
  border: 1px solid #bae6fd17;
  border-radius: 50%;
  animation: rotate 55s linear infinite;
  pointer-events: none;
}
.orbit::before, .orbit::after {
  content: "❄";
  position: absolute;
  color: var(--ice);
  font-size: 25px;
  text-shadow: 0 0 22px #7dd3fc;
}
.orbit::before { top: 10%; left: 15%; }
.orbit::after { bottom: 12%; right: 12%; }
.hero-content { position: relative; z-index: 2; animation: enter 1s ease both; }
.eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 10px 15px;
  border: 1px solid var(--line);
  border-radius: 100px;
  background: #bae6fd09;
  color: var(--ice);
  font: 10px ui-monospace, monospace;
  letter-spacing: 2px;
}
.hero h1 {
  font-size: clamp(58px, 12vw, 132px);
  letter-spacing: -.09em;
  line-height: .92;
  margin: 30px 0 22px;
  font-weight: 1000;
}
.hero h1 span {
  color: transparent;
  background: linear-gradient(110deg, #fff 5%, #bae6fd 35%, #fff 50%, #64748b 70%, #fff);
  background-size: 220% 100%;
  background-clip: text;
  -webkit-background-clip: text;
  animation: shine 7s linear infinite;
}
.hero p {
  max-width: 590px;
  margin: auto;
  line-height: 1.8;
  color: var(--muted);
  font-size: 15px;
}
.actions {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 12px;
  margin-top: 30px;
}
.btn {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  gap: 9px;
  border-radius: 12px;
  padding: 14px 20px;
  border: 1px solid var(--line);
  font-size: 12px;
  font-weight: 800;
  transition: transform .25s, background .25s, box-shadow .25s;
}
.btn:hover { transform: translateY(-4px); box-shadow: 0 10px 35px #38bdf822; }
.primary { background: var(--white); color: #030712; }
.secondary { background: #ffffff08; }
.emblem {
  width: 110px;
  height: 110px;
  margin: 30px auto 0;
  animation: float 5s ease-in-out infinite;
  filter: drop-shadow(0 0 20px #7dd3fc44);
}
.section { padding: 75px 0; }
.section-head { margin-bottom: 30px; }
.kicker {
  color: var(--ice);
  font: 10px ui-monospace, monospace;
  letter-spacing: 3px;
}
.section h2 {
  font-size: clamp(30px, 5vw, 54px);
  letter-spacing: -.05em;
  margin: 12px 0;
}
.muted { color: var(--muted); line-height: 1.8; }
.grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 15px;
}
.card {
  position: relative;
  padding: 25px;
  min-height: 190px;
  border: 1px solid var(--line);
  border-radius: 18px;
  background: linear-gradient(145deg, #ffffff0a, #ffffff02);
  overflow: hidden;
  transition: transform .3s, border-color .3s, background .3s;
}
.card::after {
  content: "";
  position: absolute;
  top: 0; left: -120%;
  height: 1px; width: 100%;
  background: linear-gradient(90deg, transparent, var(--ice), transparent);
  transition: left .7s;
}
.card:hover { transform: translateY(-7px); border-color: #bae6fd88; background: #bae6fd08; }
.card:hover::after { left: 120%; }
.card-icon {
  width: 42px;
  height: 42px;
  display: grid;
  place-items: center;
  border: 1px solid var(--line);
  border-radius: 12px;
  color: var(--ice);
  font-size: 22px;
  margin-bottom: 20px;
}
.card h3 { font-size: 16px; margin: 0 0 10px; }
.card p { color: var(--muted); font-size: 12px; line-height: 1.8; margin: 0; }
.tech {
  display: flex;
  flex-wrap: wrap;
  gap: 9px;
}
.chip {
  padding: 11px 14px;
  background: #ffffff06;
  border: 1px solid var(--line);
  border-radius: 9px;
  color: #e2e8f0;
  font: 11px ui-monospace, monospace;
}
.contact {
  padding: 35px;
  border: 1px solid var(--line);
  border-radius: 22px;
  background: radial-gradient(ellipse at top, #164e632a, transparent 70%), #ffffff04;
  text-align: center;
  animation: glow 6s ease-in-out infinite;
}
.contact h2 { font-size: clamp(30px, 5vw, 52px); margin: 15px 0; }
.contact-links {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 10px;
  margin-top: 24px;
}
footer {
  padding: 40px 0;
  text-align: center;
  color: var(--muted);
  font: 10px ui-monospace, monospace;
  letter-spacing: 2px;
}
.reveal { opacity: 0; transform: translateY(20px); transition: opacity .7s, transform .7s; }
.reveal.visible { opacity: 1; transform: translateY(0); }
@media(max-width:760px) {
  .navlinks { display: none; }
  .hero { min-height: 600px; }
  .grid { grid-template-columns: 1fr; }
  .card { min-height: 155px; }
  .section { padding: 55px 0; }
  .contact { padding: 25px 15px; }
}
@media(prefers-reduced-motion:reduce) {
  *,*::before,*::after {
    animation-duration: .01ms !important;
    animation-iteration-count: 1 !important;
    scroll-behavior: auto !important;
    transition-duration: .01ms !important;
  }
}
</style>
</head>
<body>
<canvas id="snow" aria-hidden="true"></canvas>
<div class="noise"></div>
<div class="aurora"></div>

<nav>
  <a class="logo" href="#home">HUSSI<span>DEV</span> ❄</a>
  <div class="navlinks">
    <a href="#about">About</a>
    <a href="#services">Services</a>
    <a href="#stack">Tech</a>
    <a href="#contact">Contact</a>
  </div>
  <span class="status">ARCTIC ONLINE</span>
</nav>

<main>
<section class="hero wrap" id="home">
  <div class="orbit"></div>
  <div class="hero-content">
    <div class="eyebrow">❄ FROSTBYTE EDITION · 2026</div>
    <h1><span>HUSSI<br>DEV.</span></h1>
    <p>Building the extraordinary at the intersection of code, creative engineering, AI, and futuristic design.</p>
    <div class="actions">
      <a class="btn primary" href="https://hussidev9.netlify.app/">Explore Portfolio ↗</a>
      <a class="btn secondary" href="https://hussixplugs.netlify.app/">Hussi X Plugs ❄</a>
    </div>
    <svg class="emblem" viewBox="0 0 100 100" role="img" aria-label="Animated geometric snowflake">
      <defs>
        <linearGradient id="frost" x1="0" y1="0" x2="1" y2="1">
          <stop offset="0" stop-color="#fff"/>
          <stop offset=".5" stop-color="#bae6fd"/>
          <stop offset="1" stop-color="#64748b"/>
        </linearGradient>
      </defs>
      <g fill="none" stroke="url(#frost)" stroke-width="2.5" stroke-linecap="round">
        <path d="M50 5V95 M11 27L89 73 M11 73L89 27"/>
        <path d="M50 5L43 15M50 5L57 15M50 95L43 85M50 95L57 85"/>
        <path d="M11 27L23 27M11 27L16 38M89 73L77 73M89 73L84 62"/>
        <path d="M11 73L23 73M11 73L16 62M89 27L77 27M89 27L84 38"/>
      </g>
      <circle cx="50" cy="50" r="9" fill="#f8fafc"/>
      <circle cx="50" cy="50" r="15" fill="none" stroke="#bae6fd" stroke-opacity=".4"/>
    </svg>
  </div>
</section>

<section class="section wrap reveal" id="about">
  <div class="section-head">
    <div class="kicker">01 / IDENTITY</div>
    <h2>Cold precision.<br>Bold imagination.</h2>
    <p class="muted">I'm Hussi Dev, a digital creator from Karachi, Pakistan. I develop modern web experiences, AI interfaces, automation tools, and custom digital solutions with a distinctive visual identity.</p>
  </div>
  <div class="grid">
    <article class="card">
      <div class="card-icon">❄</div>
      <h3>Design the unusual</h3>
      <p>Strong visual identities, thoughtful details, custom icons, and interfaces built to stand out.</p>
    </article>
    <article class="card">
      <div class="card-icon">⌘</div>
      <h3>Engineer with purpose</h3>
      <p>Practical websites and tools designed around real user needs and maintainable code.</p>
    </article>
    <article class="card">
      <div class="card-icon">✧</div>
      <h3>Always evolving</h3>
      <p>Experimenting with technologies, refining projects, and learning through building.</p>
    </article>
  </div>
</section>

<section class="section wrap reveal" id="services">
  <div class="section-head">
    <div class="kicker">02 / CAPABILITIES</div>
    <h2>Digital divisions.</h2>
    <p class="muted">A collection of services and project areas focused on useful, polished digital products.</p>
  </div>
  <div class="grid">
    <article class="card"><div class="card-icon">🌐</div><h3>Web development</h3><p>Responsive websites, landing pages, interactive applications, and dashboards.</p></article>
    <article class="card"><div class="card-icon">🤖</div><h3>AI & automation</h3><p>AI interfaces, assistant concepts, API integrations, and productivity tools.</p></article>
    <article class="card"><div class="card-icon">🎨</div><h3>UI/UX engineering</h3><p>Frosted-glass interfaces, custom SVG graphics, motion design, and responsive layouts.</p></article>
    <article class="card"><div class="card-icon">⚙</div><h3>Developer tools</h3><p>Utilities, coding experiments, workflow tools, and project-specific integrations.</p></article>
    <article class="card"><div class="card-icon">🛡</div><h3>Defensive security</h3><p>Authorized security testing, digital safety guidance, and account protection.</p></article>
    <article class="card"><div class="card-icon">◈</div><h3>Business solutions</h3><p>Client portals, custom business interfaces, and digital workflow systems.</p></article>
  </div>
</section>

<section class="section wrap reveal" id="stack">
  <div class="section-head">
    <div class="kicker">03 / TECHNOLOGY</div>
    <h2>The build matrix.</h2>
    <p class="muted">Technologies used or explored across development projects.</p>
  </div>
  <div class="tech">
    <span class="chip">HTML5</span><span class="chip">CSS3</span>
    <span class="chip">JavaScript</span><span class="chip">Python</span>
    <span class="chip">React</span><span class="chip">Node.js</span>
    <span class="chip">Git</span><span class="chip">GitHub</span>
    <span class="chip">REST APIs</span><span class="chip">SVG</span>
    <span class="chip">Responsive UI</span><span class="chip">Automation</span>
  </div>
</section>

<section class="section wrap reveal" id="contact">
  <div class="contact">
    <div class="kicker">04 / ESTABLISH CONNECTION</div>
    <h2>Let's build<br>something unreal.</h2>
    <p class="muted">Have a project, collaboration, or business inquiry? Reach out through one of the channels below.</p>
    <div class="contact-links">
      <a class="btn primary" href="mailto:hussidevv@gmail.com">✉ Business Email</a>
      <a class="btn secondary" href="https://wa.me/923203405324">WhatsApp ↗</a>
      <a class="btn secondary" href="https://t.me/itzhussi">Telegram ↗</a>
      <a class="btn secondary" href="https://github.com/hussixdev">GitHub ↗</a>
      <a class="btn secondary" href="https://www.tiktok.com/@itz_hussi2">TikTok ↗</a>
    </div>
    <p class="muted">📍 Karachi, Pakistan</p>
  </div>
</section>
</main>

<footer>
  <div>❄ HUSSI DEV · ARCTIC OS</div>
  <p>DESIGNED WITH CURIOSITY · BUILT TO EVOLVE</p>
  <div>© <span id="year"></span> · END OF TRANSMISSION</div>
</footer>

<script>
(() => {
  "use strict";

  const canvas = document.getElementById("snow");
  const ctx = canvas.getContext("2d");
  const reducedMotion = window.matchMedia("(prefers-reduced-motion: reduce)");
  let width = 0;
  let height = 0;
  let flakes = [];
  let animationFrame = 0;

  function resize() {
    const dpr = Math.min(window.devicePixelRatio || 1, 2);
    width = window.innerWidth;
    height = window.innerHeight;
    canvas.width = width * dpr;
    canvas.height = height * dpr;
    canvas.style.width = width + "px";
    canvas.style.height = height + "px";
    ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
    createFlakes();
  }

  function createFlakes() {
    const count = reducedMotion.matches
      ? 0
      : Math.min(150, Math.floor(width / 8));
    flakes = Array.from({ length: count }, () => ({
      x: Math.random() * width,
      y: Math.random() * height,
      r: Math.random() * 2.4 + .4,
      speed: Math.random() * .8 + .25,
      drift: (Math.random() - .5) * .55,
      alpha: Math.random() * .65 + .2,
      phase: Math.random() * Math.PI * 2
    }));
  }

  function drawSnow() {
    ctx.clearRect(0, 0, width, height);
    for (const f of flakes) {
      f.y += f.speed;
      f.x += f.drift + Math.sin(f.phase += .008) * .25;
      if (f.y > height + 5) {
        f.y = -5;
        f.x = Math.random() * width;
      }
      if (f.x > width + 5) f.x = -5;
      if (f.x < -5) f.x = width + 5;

      ctx.beginPath();
      ctx.arc(f.x, f.y, f.r, 0, Math.PI * 2);
      ctx.fillStyle = `rgba(224,242,254,${f.alpha})`;
      ctx.shadowBlur = f.r > 1.8 ? 8 : 0;
      ctx.shadowColor = "#bae6fd";
      ctx.fill();
    }
    ctx.shadowBlur = 0;
    if (!reducedMotion.matches) {
      animationFrame = requestAnimationFrame(drawSnow);
    }
  }

  function startSnow() {
    cancelAnimationFrame(animationFrame);
    ctx.clearRect(0, 0, width, height);
    if (!reducedMotion.matches) drawSnow();
  }

  window.addEventListener("resize", resize, { passive: true });
  reducedMotion.addEventListener?.("change", () => {
    createFlakes();
    startSnow();
  });

  resize();
  startSnow();

  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add("visible");
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: .12 });

  document.querySelectorAll(".reveal").forEach(el => observer.observe(el));
  document.getElementById("year").textContent = new Date().getFullYear();
})();
</script>
</body>
</html>

