<!DOCTYPE html>
<html lang="ro">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NEXUS://ART — Cultura Informațională & Animație</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700;900&family=Share+Tech+Mono&display=swap" rel="stylesheet">
<style>
:root{
  --cyan:#00f0ff;
  --pink:#ff2d78;
  --yellow:#f6ff00;
  --bg:#05060a;
  --panel:rgba(8,12,22,.78);
  --line:rgba(0,240,255,.22);
}
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}
body{
  background:var(--bg);
  color:#cfeeff;
  font-family:'Share Tech Mono',monospace;
  overflow-x:hidden;
}

/* ===== PLOAIE MATRIX (fundal) ===== */
#matrix{position:fixed;inset:0;z-index:0;opacity:.13;pointer-events:none}

/* ===== SCANLINES + VIGNETĂ ===== */
body::before{
  content:"";position:fixed;inset:0;z-index:50;pointer-events:none;
  background:repeating-linear-gradient(0deg,rgba(0,0,0,.22) 0 1px,transparent 1px 3px);
}
body::after{
  content:"";position:fixed;inset:0;z-index:51;pointer-events:none;
  background:radial-gradient(ellipse at center,transparent 55%,rgba(0,0,10,.55) 100%);
}

/* ===== NAV ===== */
nav{
  position:sticky;top:0;z-index:60;
  display:flex;align-items:center;gap:1.4rem;flex-wrap:wrap;
  padding:.9rem 1.5rem;
  background:rgba(5,6,10,.85);backdrop-filter:blur(8px);
  border-bottom:1px solid var(--line);
}
.logo{
  font-family:'Orbitron',sans-serif;font-weight:900;letter-spacing:.12em;
  color:var(--cyan);text-shadow:0 0 8px var(--cyan);
  margin-right:auto;user-select:none;
}
.logo span{color:var(--pink);text-shadow:0 0 8px var(--pink)}
nav a{
  color:var(--cyan);text-decoration:none;font-size:.95rem;transition:.2s;
}
nav a::before{content:">";margin-right:.35em;opacity:.35}
nav a:hover{color:var(--yellow);text-shadow:0 0 10px var(--yellow)}
nav a:hover::before{opacity:1}

/* ===== HERO ===== */
header{
  position:relative;z-index:1;min-height:92vh;
  display:flex;flex-direction:column;justify-content:center;align-items:center;
  text-align:center;padding:4rem 1.5rem;
  background:
    linear-gradient(rgba(5,6,10,.55),rgba(5,6,10,.92)),
    repeating-linear-gradient(90deg,transparent 0 118px,rgba(0,240,255,.05) 118px 119px),
    repeating-linear-gradient(0deg,transparent 0 118px,rgba(0,240,255,.05) 118px 119px);
}
.sys-msg{
  color:var(--yellow);font-size:.8rem;letter-spacing:.25em;
  border:1px solid rgba(246,255,0,.35);padding:.4rem 1rem;margin-bottom:2rem;
  clip-path:polygon(10px 0,100% 0,100% calc(100% - 10px),calc(100% - 10px) 100%,0 100%,0 10px);
}
h1.glitch{
  font-family:'Orbitron',sans-serif;font-weight:900;
  font-size:clamp(2rem,7vw,4.6rem);line-height:1.1;color:#fff;
  position:relative;z-index:0;
  text-shadow:0 0 18px rgba(0,240,255,.55);
}
h1.glitch::before,h1.glitch::after{content:attr(data-text);position:absolute;inset:0}
h1.glitch::before{color:var(--pink);z-index:-1;animation:gl1 2.4s infinite steps(2,end)}
h1.glitch::after{color:var(--cyan);z-index:-2;animation:gl2 3.1s infinite steps(2,end)}
@keyframes gl1{
  0%,100%{transform:translate(0)}
  20%{transform:translate(-3px,2px)}
  40%{transform:translate(3px,-1px)}
  60%{transform:translate(-2px,-2px)}
  80%{transform:translate(2px,1px)}
}
@keyframes gl2{
  0%,100%{transform:translate(0)}
  25%{transform:translate(3px,1px)}
  50%{transform:translate(-3px,2px)}
  75%{transform:translate(1px,-2px)}
}
.typeline{
  margin-top:1.6rem;font-size:clamp(.9rem,2.2vw,1.1rem);
  color:var(--cyan);letter-spacing:.06em;min-height:1.6em;
}
.cursor{
  display:inline-block;width:.6em;height:1.1em;background:var(--cyan);
  vertical-align:text-bottom;animation:blink 1s steps(1) infinite;
}
@keyframes blink{50%{opacity:0}}
.cta{
  margin-top:2.6rem;display:inline-block;
  font-family:'Orbitron',sans-serif;font-weight:700;
  color:var(--bg);background:var(--cyan);
  padding:.9rem 2.2rem;text-decoration:none;letter-spacing:.15em;
  clip-path:polygon(14px 0,100% 0,100% calc(100% - 14px),calc(100% - 14px) 100%,0 100%,0 14px);
  box-shadow:0 0 18px rgba(0,240,255,.6);transition:.2s;
}
.cta:hover{background:var(--pink);color:#fff;box-shadow:0 0 24px rgba(255,45,120,.8)}

/* ===== SECȚIUNI ===== */
section{position:relative;z-index:1;max-width:1000px;margin:0 auto;padding:5rem 1.5rem}
.sec-tag{color:var(--pink);letter-spacing:.3em;font-size:.8rem;margin-bottom:.6rem}
h2{
  font-family:'Orbitron',sans-serif;font-weight:700;color:#fff;
  font-size:clamp(1.4rem,3.5vw,2rem);margin-bottom:1.2rem;
  text-shadow:0 0 12px rgba(0,240,255,.4);
}
h2::before{content:"//";color:var(--cyan);margin-right:.5rem}
.lead{max-width:720px;margin-bottom:2.2rem;line-height:1.8;color:#9fd8e8}

.grid{display:grid;gap:1.2rem;grid-template-columns:repeat(auto-fit,minmax(250px,1fr))}
.card{
  background:var(--panel);border:1px solid var(--line);
  padding:1.4rem 1.3rem;position:relative;transition:.25s;
  clip-path:polygon(16px 0,100% 0,100% calc(100% - 16px),calc(100% - 16px) 100%,0 100%,0 16px);
}
.card::before{
  content:"";position:absolute;top:0;left:0;width:42px;height:3px;
  background:var(--cyan);box-shadow:0 0 10px var(--cyan);
}
.card:hover{
  border-color:var(--pink);transform:translateY(-4px);
  box-shadow:0 8px 30px rgba(255,45,120,.25);
}
.card:hover::before{background:var(--pink);box-shadow:0 0 10px var(--pink)}
.card h3{
  font-family:'Orbitron',sans-serif;font-size:.95rem;
  color:var(--cyan);margin-bottom:.7rem;letter-spacing:.05em;
}
.card p{font-size:.92rem;line-height:1.65;color:#a8cfdd}

/* ===== TERMINAL ===== */
.term{background:#02040a;border:1px solid var(--line);box-shadow:inset 0 0 30px rgba(0,240,255,.07)}
.term-bar{display:flex;gap:.45rem;align-items:center;padding:.7rem 1rem;border-bottom:1px solid var(--line)}
.dot{width:11px;height:11px;border-radius:50%}
.dot.r{background:#ff5f56}.dot.y{background:#ffbd2e}.dot.g{background:#27c93f}
.term-title{margin-left:auto;font-size:.75rem;color:#5f8ea0;letter-spacing:.15em}
.term-body{padding:1.2rem 1.4rem;font-size:.92rem;line-height:2}
.term-body .ok{color:#27c93f}
.term-body .cmd{color:var(--pink)}
.term-body .res{color:#cfeeff}

/* ===== STATISTICI ===== */
.stat-row{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:1.2rem;margin-top:2.5rem}
.stat{border:1px solid var(--line);background:var(--panel);text-align:center;padding:1.6rem 1rem;transition:.25s}
.stat:hover{border-color:var(--yellow);box-shadow:0 0 18px rgba(246,255,0,.2)}
.stat b{
  display:block;font-family:'Orbitron',sans-serif;font-size:1.8rem;
  color:var(--yellow);text-shadow:0 0 12px rgba(246,255,0,.5);
}
.stat span{font-size:.8rem;color:#7fb6c7;letter-spacing:.15em}

footer{
  position:relative;z-index:1;border-top:1px solid var(--line);
  background:rgba(5,6,10,.9);text-align:center;padding:2.4rem 1.5rem;
  color:#5f8ea0;font-size:.85rem;letter-spacing:.1em;line-height:2;
}
footer .neon{color:var(--cyan);text-shadow:0 0 8px var(--cyan)}

/* ===== ANIMAȚIE LA SCROLL ===== */
.reveal{opacity:0;transform:translateY(28px);transition:opacity .7s ease,transform .7s ease}
.reveal.on{opacity:1;transform:none}

@media (prefers-reduced-motion:reduce){
  *,*::before,*::after{animation:none!important;transition:none!important}
  html{scroll-behavior:auto}
  .reveal{opacity:1;transform:none}
}
</style>
</head>
<body>

<canvas id="matrix" aria-hidden="true"></canvas>

<nav>
  <div class="logo">NEXUS<span>://</span>ART</div>
  <a href="#acasa">HOME</a>
  <a href="#cultura">CULTURA_INFO</a>
  <a href="#artist">ROL_ARTIST</a>
  <a href="#animatie">ANIMATIE</a>
</nav>

<header id="acasa">
  <div class="sys-msg">SYS.MSG // PROIECT EDUCAȚIONAL ONLINE</div>
  <h1 class="glitch" data-text="NEXUS://ART">NEXUS://ART</h1>
  <p class="typeline"><span id="typed"></span><span class="cursor"></span></p>
  <a class="cta" href="#cultura">INIȚIAZĂ PROTOCOLUL ▸</a>
</header>

<section id="cultura">
  <div class="sec-tag">MODULE_01</div>
  <h2>CULTURA INFORMAȚIONALĂ ȘI TEHNOLOGIA</h2>
  <p class="lead">Cultura informațională = capacitatea de a recunoaște când ai nevoie de informație, de a o localiza, evalua critic și folosi în mod etic și eficient. În era digitală, este skill-ul de bază al oricărui creator.</p>
  <div class="grid">
    <div class="card reveal">
      <h3>ALFABETIZARE DIGITALĂ</h3>
      <p>Utilizarea competentă a instrumentelor tehnologice: de la editoare de text la software de animație 3D și platforme AI.</p>
    </div>
    <div class="card reveal">
      <h3>GÂNDIRE CRITICĂ</h3>
      <p>Evaluarea credibilității surselor — esențială în era știrilor false și a conținutului generat automat de AI.</p>
    </div>
    <div class="card reveal">
      <h3>ETICA INFORMAȚIEI</h3>
      <p>Plagiatul, drepturile de autor și utilizarea responsabilă a AI fac parte din codul onoarei artistului digital.</p>
    </div>
    <div class="card reveal">
      <h3>ADAPTABILITATE</h3>
      <p>Tehnologia evoluează constant. Cultura informațională înseamnă învățare continuă și actualizare permanentă.</p>
    </div>
  </div>
</section>

<section id="artist">
  <div class="sec-tag">MODULE_02</div>
  <h2>ROLUL ARTISTULUI ÎN ERA DIGITALĂ</h2>
  <p class="lead">Artistul contemporan nu mai este doar creator — este și navigator al fluxului informațional. Rulează diagnosticul:</p>
  <div class="term reveal">
    <div class="term-bar">
      <span class="dot r"></span><span class="dot y"></span><span class="dot g"></span>
      <span class="term-title">artist_rol.sh — bash</span>
    </div>
    <div class="term-body">
      <div><span class="cmd">$ scan --rol-artist-digital</span></div>
      <div><span class="ok">[OK]</span> <span class="res">CURATOR_DE_INFORMAȚIE .... transformă fluxul digital în operă de artă</span></div>
      <div><span class="ok">[OK]</span> <span class="res">COLABORATOR_TEHNOLOGIE ... AI & software = extensii ale creativității</span></div>
      <div><span class="ok">[OK]</span> <span class="res">AGENT_ETIC ............... folosește responsabil instrumentele digitale</span></div>
      <div><span class="ok">[OK]</span> <span class="res">EDUCATOR_CULTURAL ........ influențează percepția realității digitale</span></div>
      <div><span class="cmd">$ status --creativitate</span> <span class="ok">■ ONLINE</span></div>
    </div>
  </div>
</section>

<section id="animatie">
  <div class="sec-tag">MODULE_03</div>
  <h2>TEHNOLOGIA ÎN SERVICIUL ANIMAȚIEI</h2>
  <p class="lead">Cultura informațională îl ajută pe animator să învețe mai repede, să găsească resurse de calitate și să colaboreze global. Arsenalul complet:</p>
  <div class="grid">
    <div class="card reveal">
      <h3>ÎNVĂȚARE</h3>
      <p>Tutoriale YouTube, cursuri online (Coursera, Skillshare), documentație oficială — cunoașterea este open-source.</p>
    </div>
    <div class="card reveal">
      <h3>INSTRUMENTE</h3>
      <p>Blender (gratuit), Toon Boom Harmony, Adobe Animate, After Effects, TVPaint.</p>
    </div>
    <div class="card reveal">
      <h3>COMUNITĂȚI</h3>
      <p>ArtStation, Behance, Discord, Reddit — feedback instant de la artiști din toată lumea.</p>
    </div>
    <div class="card reveal">
      <h3>AI CA ASISTENT</h3>
      <p>Generare de concepte, in-betweening automat, rotoscoping asistat. Artistul rămâne directorul creativ.</p>
    </div>
  </div>
  <div class="stat-row">
    <div class="stat reveal"><b>24/7</b><span>ACCES LA CUNOAȘTERE</span></div>
    <div class="stat reveal"><b>∞</b><span>ITERAȚII CREATIVE</span></div>
    <div class="stat reveal"><b>x10</b><span>VITEZĂ DE ÎNVĂȚARE</span></div>
    <div class="stat reveal"><b>1</b><span>DIRECTOR CREATIV: TU</span></div>
  </div>
</section>

<footer>
  <p>[ NEXUS://ART ] © 2025 — proiect educațional despre cultura informațională și animație</p>
  <p>build v2.0_cyberpunk // găzduit pe <span class="neon">GitHub Pages</span></p>
</footer>

<script>
const reduce = matchMedia('(prefers-reduced-motion: reduce)').matches;

/* Ploaie Matrix */
const cv = document.getElementById('matrix'), cx = cv.getContext('2d');
const glyphs = 'アイウエオカキクケコサシスセソ01#$%&*+=NEXUSART'.split('');
let W, H, drops;
function size(){
  W = cv.width = innerWidth;
  H = cv.height = innerHeight;
  drops = Array(Math.floor(W/16)).fill(0).map(() => Math.random()*H/16 | 0);
}
size(); addEventListener('resize', size);
if(!reduce){
  setInterval(() => {
    cx.fillStyle = 'rgba(5,6,10,.08)';
    cx.fillRect(0,0,W,H);
    cx.fillStyle = '#00f0ff';
    cx.font = '14px monospace';
    drops.forEach((y,i) => {
      cx.fillText(glyphs[Math.random()*glyphs.length|0], i*16, y*16);
      if(y*16 > H && Math.random() > .975) drops[i] = 0;
      drops[i]++;
    });
  }, 66);
}

/* Efect de tastare în hero */
const lines = [
  'conectare la rețeaua cunoașterii... OK',
  'încărcare modul: cultura informațională ✔',
  'încărcare modul: rolul artistului ✔',
  'încărcare modul: tehnologia animației ✔',
  'sistem pregătit. bun venit, creatorule_'
];
const typed = document.getElementById('typed');
let li = 0, ci = 0;
(function type(){
  if(reduce){ typed.textContent = lines[lines.length-1]; return; }
  if(li >= lines.length) return;
  typed.textContent = lines[li].slice(0, ++ci);
  if(ci < lines[li].length) setTimeout(type, 34);
  else setTimeout(() => { li++; ci = 0; type(); }, 900);
})();

/* Apariție la scroll */
const io = new IntersectionObserver(es => es.forEach(e => {
  if(e.isIntersecting){ e.target.classList.add('on'); io.unobserve(e.target); }
}), {threshold:.15});
document.querySelectorAll('.reveal').forEach(el => io.observe(el));
</script>
</body>
</html>
