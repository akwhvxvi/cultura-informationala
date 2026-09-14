<html lang="ro">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Proiect educațional: cultura informațională, tehnologia și rolul artistului în animație.">
<title>NEXUS://ART — Cultura Informațională & Animație</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700;900&family=Share+Tech+Mono&display=swap" rel="stylesheet">
<style>
/* ===== TEME (comutabile) ===== */
:root, body[data-theme="cyber"]{
  --acc1:#00f0ff; --acc2:#ff2d78; --acc3:#f6ff00;
  --bg:#05060a; --panel:rgba(8,12,22,.78); --line:rgba(0,240,255,.22);
  --text:#cfeeff; --lead:#9fd8e8; --muted:#5f8ea0;
}
body[data-theme="matrix"]{
  --acc1:#00ff41; --acc2:#ffb000; --acc3:#d4ff9e;
  --panel:rgba(4,18,8,.78); --line:rgba(0,255,65,.25);
  --text:#c9f7d6; --lead:#8fd6a5; --muted:#6aa884;
}
body[data-theme="synth"]{
  --acc1:#c724ff; --acc2:#ff2d78; --acc3:#ffe867;
  --panel:rgba(16,6,26,.78); --line:rgba(199,36,255,.28);
  --text:#f2e3ff; --lead:#c9a8e8; --muted:#9a7fb8;
}
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}
body{
  background:var(--bg); color:var(--text);
  font-family:'Share Tech Mono',monospace; overflow-x:hidden;
}
section,header{scroll-margin-top:70px}

/* ===== PLOAIE MATRIX ===== */
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
  display:flex;align-items:center;gap:1.3rem;flex-wrap:wrap;
  padding:.9rem 1.5rem;
  background:rgba(5,6,10,.85);backdrop-filter:blur(8px);
  border-bottom:1px solid var(--line);
}
.logo{
  font-family:'Orbitron',sans-serif;font-weight:900;letter-spacing:.12em;
  color:var(--acc1);text-shadow:0 0 8px var(--acc1);
  margin-right:auto;user-select:none;
}
.logo span{color:var(--acc2);text-shadow:0 0 8px var(--acc2)}
nav a{color:var(--acc1);text-decoration:none;font-size:.95rem;transition:.2s}
nav a::before{content:">";margin-right:.35em;opacity:.35}
nav a:hover{color:var(--acc3);text-shadow:0 0 10px var(--acc3)}
nav a:hover::before{opacity:1}
.themes{display:flex;align-items:center;gap:.5rem}
.themes-label{font-size:.7rem;color:var(--muted);letter-spacing:.2em}
.theme-btn{
  width:20px;height:20px;border:1px solid rgba(255,255,255,.3);
  cursor:pointer;transition:.2s;padding:0;
}
.theme-btn[data-theme="cyber"]{background:#00f0ff}
.theme-btn[data-theme="matrix"]{background:#00ff41}
.theme-btn[data-theme="synth"]{background:#c724ff}
.theme-btn.active{
  box-shadow:0 0 0 2px var(--bg),0 0 0 3px #fff,0 0 10px rgba(255,255,255,.6);
  transform:scale(1.1);
}

/* ===== HERO ===== */
header{
  position:relative;z-index:1;min-height:92vh;
  display:flex;flex-direction:column;justify-content:center;align-items:center;
  text-align:center;padding:4rem 1.5rem;
  background:
    linear-gradient(rgba(5,6,10,.55),rgba(5,6,10,.92)),
    repeating-linear-gradient(90deg,transparent 0 118px,rgba(255,255,255,.04) 118px 119px),
    repeating-linear-gradient(0deg,transparent 0 118px,rgba(255,255,255,.04) 118px 119px);
}
.sys-msg{
  color:var(--acc3);font-size:.8rem;letter-spacing:.25em;
  border:1px solid var(--acc3);padding:.4rem 1rem;margin-bottom:2rem;
  clip-path:polygon(10px 0,100% 0,100% calc(100% - 10px),calc(100% - 10px) 100%,0 100%,0 10px);
}
h1.glitch{
  font-family:'Orbitron',sans-serif;font-weight:900;
  font-size:clamp(2rem,7vw,4.6rem);line-height:1.1;color:#fff;
  position:relative;z-index:0;text-shadow:0 0 18px var(--acc1);
}
h1.glitch::before,h1.glitch::after{content:attr(data-text);position:absolute;inset:0}
h1.glitch::before{color:var(--acc2);z-index:-1;animation:gl1 2.4s infinite steps(2,end)}
h1.glitch::after{color:var(--acc1);z-index:-2;animation:gl2 3.1s infinite steps(2,end)}
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
  color:var(--acc1);letter-spacing:.06em;min-height:1.6em;
}
.cursor{
  display:inline-block;width:.6em;height:1.1em;background:var(--acc1);
  vertical-align:text-bottom;animation:blink 1s steps(1) infinite;
}
@keyframes blink{50%{opacity:0}}
.cta{
  margin-top:2.6rem;display:inline-block;
  font-family:'Orbitron',sans-serif;font-weight:700;
  color:var(--bg);background:var(--acc1);
  padding:.9rem 2.2rem;text-decoration:none;letter-spacing:.15em;
  clip-path:polygon(14px 0,100% 0,100% calc(100% - 14px),calc(100% - 14px) 100%,0 100%,0 14px);
  box-shadow:0 0 18px var(--acc1);transition:.2s;
}
.cta:hover{background:var(--acc2);color:#fff;box-shadow:0 0 24px var(--acc2)}

/* ===== SECȚIUNI ===== */
section{position:relative;z-index:1;max-width:1000px;margin:0 auto;padding:5rem 1.5rem}
.sec-tag{color:var(--acc2);letter-spacing:.3em;font-size:.8rem;margin-bottom:.6rem}
h2{
  font-family:'Orbitron',sans-serif;font-weight:700;color:#fff;
  font-size:clamp(1.4rem,3.5vw,2rem);margin-bottom:1.2rem;
  text-shadow:0 0 12px var(--acc1);
}
h2::before{content:"//";color:var(--acc1);margin-right:.5rem}
.lead{max-width:720px;margin-bottom:2.2rem;line-height:1.8;color:var(--lead)}

.grid{display:grid;gap:1.2rem;grid-template-columns:repeat(auto-fit,minmax(250px,1fr))}
.card{
  background:var(--panel);border:1px solid var(--line);
  padding:1.4rem 1.3rem;position:relative;transition:.25s;
  clip-path:polygon(16px 0,100% 0,100% calc(100% - 16px),calc(100% - 16px) 100%,0 100%,0 16px);
}
.card::before{
  content:"";position:absolute;top:0;left:0;width:42px;height:3px;
  background:var(--acc1);box-shadow:0 0 10px var(--acc1);
}
.card:hover{
  border-color:var(--acc2);transform:translateY(-4px);
  box-shadow:0 8px 30px var(--acc2);
}
.card:hover::before{background:var(--acc2);box-shadow:0 0 10px var(--acc2)}
.card h3{
  font-family:'Orbitron',sans-serif;font-size:.95rem;
  color:var(--acc1);margin-bottom:.7rem;letter-spacing:.05em;
}
.card p{font-size:.92rem;line-height:1.65;color:var(--lead)}

/* ===== TERMINAL ===== */
.term{background:#02040a;border:1px solid var(--line);box-shadow:inset 0 0 30px var(--line)}
.term-bar{display:flex;gap:.45rem;align-items:center;padding:.7rem 1rem;border-bottom:1px solid var(--line)}
.dot{width:11px;height:11px;border-radius:50%}
.dot.r{background:#ff5f56}.dot.y{background:#ffbd2e}.dot.g{background:#27c93f}
.term-title{margin-left:auto;font-size:.75rem;color:var(--muted);letter-spacing:.15em}
.term-body{padding:1.2rem 1.4rem;font-size:.92rem;line-height:2}
.term-body .ok{color:#27c93f}
.term-body .cmd{color:var(--acc2)}
.term-body .res{color:var(--text)}

/* ===== STATISTICI ===== */
.stat-row{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:1.2rem;margin-top:2.5rem}
.stat{border:1px solid var(--line);background:var(--panel);text-align:center;padding:1.6rem 1rem;transition:.25s}
.stat:hover{border-color:var(--acc3);box-shadow:0 0 18px var(--acc3)}
.stat b{
  display:block;font-family:'Orbitron',sans-serif;font-size:1.8rem;
  color:var(--acc3);text-shadow:0 0 12px var(--acc3);
}
.stat span{font-size:.8rem;color:var(--muted);letter-spacing:.15em}

/* ===== CRONOLOGIE ===== */
.timeline{position:relative;margin-top:2.5rem;padding:.5rem 0}
.timeline::before{
  content:"";position:absolute;left:50%;top:0;bottom:0;width:2px;
  background:var(--acc1);opacity:.4;box-shadow:0 0 8px var(--acc1);
  transform:translateX(-50%);
}
.tl-item{position:relative;width:50%;padding:1rem 2.6rem 2.6rem}
.tl-item:nth-child(odd){left:0;text-align:right}
.tl-item:nth-child(even){left:50%;text-align:left}
.tl-item::before{
  content:"";position:absolute;top:1.7rem;width:13px;height:13px;
  background:var(--bg);border:2px solid var(--acc1);
  box-shadow:0 0 10px var(--acc1);transform:rotate(45deg);
}
.tl-item:nth-child(odd)::before{right:-7px}
.tl-item:nth-child(even)::before{left:-7px}
.tl-year{
  font-family:'Orbitron',sans-serif;font-weight:900;font-size:1.5rem;
  color:var(--acc1);text-shadow:0 0 12px var(--acc1);margin-bottom:.5rem;
}
.tl-card{
  display:inline-block;background:var(--panel);border:1px solid var(--line);
  padding:1.1rem 1.2rem;text-align:left;max-width:400px;transition:.25s;
}
.tl-card:hover{border-color:var(--acc2);box-shadow:0 6px 24px var(--acc2)}
.tl-card h3{
  font-family:'Orbitron',sans-serif;font-size:.9rem;
  color:var(--acc2);margin-bottom:.5rem;letter-spacing:.05em;
}
.tl-card p{font-size:.88rem;line-height:1.6;color:var(--lead)}
@media (max-width:720px){
  .timeline::before{left:10px;transform:none}
  .tl-item{width:100%;left:0!important;text-align:left!important;padding:0 0 2.4rem 2.4rem}
  .tl-item::before{left:4px!important;right:auto!important}
}

/* ===== QUIZ ===== */
.q-text{color:var(--text);margin:1rem 0 .8rem;font-size:1.08rem;line-height:1.6}
.q-answers{margin:.5rem 0}
.q-ans{
  display:block;width:100%;text-align:left;
  background:rgba(255,255,255,.03);border:1px solid var(--line);
  color:var(--text);padding:.8rem 1rem;margin:.55rem 0;cursor:pointer;
  font-family:inherit;font-size:.92rem;transition:.2s;line-height:1.5;
}
.q-ans:hover:not(:disabled){border-color:var(--acc1);color:var(--acc1);transform:translateX(4px)}
.q-ans:disabled{cursor:default;opacity:.45}
.q-ans.correct{border-color:#27c93f;color:#27c93f;background:rgba(39,201,63,.1);opacity:1}
.q-ans.wrong{border-color:var(--acc2);color:var(--acc2);background:rgba(255,45,120,.1);opacity:1}
.q-feedback{min-height:1.6em;font-size:.9rem;margin-top:.6rem}
.q-feedback.good{color:#27c93f}
.q-feedback.bad{color:var(--acc2)}
.q-next,.q-restart{
  margin-top:1rem;font-family:'Orbitron',sans-serif;font-weight:700;
  background:var(--acc1);color:var(--bg);border:0;padding:.6rem 1.5rem;
  cursor:pointer;letter-spacing:.12em;font-size:.85rem;transition:.2s;
}
.q-next:hover,.q-restart:hover{background:var(--acc2);color:#fff}
.res-big{
  font-family:'Orbitron',sans-serif;font-weight:900;font-size:1.7rem;
  color:var(--acc3);text-shadow:0 0 14px var(--acc3);margin:1rem 0 .5rem;
}
.res-bar{color:var(--acc1);font-size:1.1rem;letter-spacing:.1em;text-shadow:0 0 8px var(--acc1)}
.res-rank{color:var(--acc1);font-size:1.05rem;margin:.8rem 0 .4rem}
.res-msg{color:var(--lead);line-height:1.7}

footer{
  position:relative;z-index:1;border-top:1px solid var(--line);
  background:rgba(5,6,10,.9);text-align:center;padding:2.4rem 1.5rem;
  color:var(--muted);font-size:.85rem;letter-spacing:.1em;line-height:2;
}
footer .neon{color:var(--acc1);text-shadow:0 0 8px var(--acc1)}

/* ===== APARIȚIE LA SCROLL ===== */
.reveal{opacity:0;transform:translateY(28px);transition:opacity .7s ease,transform .7s ease}
.reveal.on{opacity:1;transform:none}

@media (prefers-reduced-motion:reduce){
  *,*::before,*::after{animation:none!important;transition:none!important}
  html{scroll-behavior:auto}
  .reveal{opacity:1;transform:none}
}
</style>
</head>
<body data-theme="cyber">

<canvas id="matrix" aria-hidden="true"></canvas>

<nav>
  <div class="logo">NEXUS<span>://</span>ART</div>
  <a href="#acasa">HOME</a>
  <a href="#cultura">CULTURA_INFO</a>
  <a href="#artist">ROL_ARTIST</a>
  <a href="#animatie">ANIMATIE</a>
  <a href="#timeline">TIMELINE</a>
  <a href="#quiz">QUIZ</a>
  <div class="themes">
    <span class="themes-label">TEMA:</span>
    <button class="theme-btn" data-theme="cyber"  title="Cyber Cyan"  aria-label="Temă cyan"></button>
    <button class="theme-btn" data-theme="matrix" title="Matrix Green" aria-label="Temă verde"></button>
    <button class="theme-btn" data-theme="synth"  title="Synthwave"    aria-label="Temă synthwave"></button>
  </div>
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

<section id="timeline">
  <div class="sec-tag">MODULE_04</div>
  <h2>EVOLUȚIA ANIMAȚIEI: DE LA ZOOTROP LA AI</h2>
  <p class="lead">Fiecare salt tehnologic a redefinit arta mișcării. Urmărește firul neon al istoriei:</p>
  <div class="timeline">
    <div class="tl-item reveal">
      <div class="tl-year">1832</div>
      <div class="tl-card">
        <h3>FENAKISTOSCOPUL & ZOOTROPUL</h3>
        <p>Primele dispozitive opticе care creează iluzia mișcării din imagini statice. Tehnologia naște animația.</p>
      </div>
    </div>
    <div class="tl-item reveal">
      <div class="tl-year">1928</div>
      <div class="tl-card">
        <h3>STEAMBOAT WILLIE</h3>
        <p>Mickey Mouse debutează cu sunet sincronizat. Tehnologia audio transformă desenele animate în fenomen cultural.</p>
      </div>
    </div>
    <div class="tl-item reveal">
      <div class="tl-year">1937</div>
      <div class="tl-card">
        <h3>ALBĂ CA ZĂPADA</h3>
        <p>Primul lungmetraj animat clasic, realizat cu camera multiplan. Animația devine artă majoră.</p>
      </div>
    </div>
    <div class="tl-item reveal">
      <div class="tl-year">1995</div>
      <div class="tl-card">
        <h3>TOY STORY</h3>
        <p>Pixar lansează primul lungmetraj integral generat pe calculator (CGI). Desenul pe hârtie nu mai e singura cale.</p>
      </div>
    </div>
    <div class="tl-item reveal">
      <div class="tl-year">2001</div>
      <div class="tl-card">
        <h3>SHREK</h3>
        <p>Primul câștigător al Oscarului pentru cel mai bun film animat — CGI-ul cucerește critica internațională.</p>
      </div>
    </div>
    <div class="tl-item reveal">
      <div class="tl-year">2018</div>
      <div class="tl-card">
        <h3>SPIDER-VERSE</h3>
        <p>Fuziunea dintre grafica comicelor (linii, halftone) și tehnologia 3D: un limbaj vizual complet nou.</p>
      </div>
    </div>
    <div class="tl-item reveal">
      <div class="tl-year">2022+</div>
      <div class="tl-card">
        <h3>ERA AI</h3>
        <p>Instrumente generative intră în fluxul de producție. Cultura informațională devine superputerea artistului.</p>
      </div>
    </div>
  </div>
</section>

<section id="quiz">
  <div class="sec-tag">MODULE_05</div>
  <h2>TESTEAZĂ-ȚI CULTURA INFORMATIONALĂ</h2>
  <p class="lead">Șase întrebări, fără presiune. Sistemul îți calculează rangul la final. Spor!</p>
  <div class="term reveal" id="quiz-box"></div>
</section>

<footer>
  <p>[ NEXUS://ART ] © 2025 — proiect educațional despre cultura informațională și animație</p>
  <p>build v3.0_cyberpunk // găzduit pe <span class="neon">GitHub Pages</span></p>
</footer>

<script>
const reduce = matchMedia('(prefers-reduced-motion: reduce)').matches;

/* ===== COMUTATOR DE TEMĂ ===== */
const RAIN = {cyber:'#00f0ff', matrix:'#00ff41', synth:'#c724ff'};
let rainColor = RAIN.cyber;

function setTheme(t){
  document.body.dataset.theme = t;
  rainColor = RAIN[t];
  document.querySelectorAll('.theme-btn').forEach(b =>
    b.classList.toggle('active', b.dataset.theme === t));
  try{ localStorage.setItem('nexus-theme', t); }catch(e){}
}
let saved = null;
try{ saved = localStorage.getItem('nexus-theme'); }catch(e){}
setTheme(saved || 'cyber');
document.querySelectorAll('.theme-btn').forEach(b =>
  b.addEventListener('click', () => setTheme(b.dataset.theme)));

/* ===== PLOAIE MATRIX ===== */
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
    cx.fillStyle = rainColor;
    cx.font = '14px monospace';
    drops.forEach((y,i) => {
      cx.fillText(glyphs[Math.random()*glyphs.length|0], i*16, y*16);
      if(y*16 > H && Math.random() > .975) drops[i] = 0;
      drops[i]++;
    });
  }, 66);
}

/* ===== EFECT DE TASTARE ===== */
const lines = [
  'conectare la rețeaua cunoașterii... OK',
  'încărcare modul: cultura informațională ✔',
  'încărcare modul: rolul artistului ✔',
  'încărcare modul: cronologia animației ✔',
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

/* ===== APARIȚIE LA SCROLL ===== */
const io = new IntersectionObserver(es => es.forEach(e => {
  if(e.isIntersecting){ e.target.classList.add('on'); io.unobserve(e.target); }
}), {threshold:.15});
document.querySelectorAll('.reveal').forEach(el => io.observe(el));

/* ===== QUIZ ===== */
const QUIZ = [
  {
    q: 'Ce reprezintă cultura informațională?',
    a: [
      'Capacitatea de a găsi, evalua și folosi informația în mod etic și eficient',
      'Numărul de rețele sociale folosite zilnic',
      'Abilitatea de a memora cât mai multe date',
      'Utilizarea exclusivă a cărților tipărite'
    ],
    c: 0
  },
  {
    q: 'Care dintre următoarele este un instrument GRATUIT de animație 3D?',
    a: ['Toon Boom Harmony', 'Blender', 'Adobe After Effects', 'TVPaint'],
    c: 1
  },
  {
    q: 'Ce înseamnă „in-betweening" în animație?',
    a: [
      'Procesul de export al fișierelor video',
      'Crearea cadrelor intermediare dintre pozițiile-cheie',
      'Adăugarea efectelor sonore',
      'Colorarea fondalurilor'
    ],
    c: 1
  },
  {
    q: 'Folosești un generator AI pentru imagini de referință. Ce abordare este ETICĂ?',
    a: [
      'Prezentarea rezultatului AI ca fiind desenul tău de mână',
      'Ignorarea drepturilor de autor ale artiștilor din setul de antrenament',
      'Verificarea licențelor și declararea utilizării AI în procesul creativ',
      'Nu există reguli — totul este permis online'
    ],
    c: 2
  },
  {
    q: 'Găsești un tutorial de animație pe YouTube. Care este primul pas CRITIC?',
    a: [
      'Evaluarea credibilității sursei: autor, recenzii, calitatea demonstrațiilor',
      'Urmărirea până la capăt fără a analiza calitatea',
      'Copierea rezultatului fără a înțelege tehnica',
      'Alegerea mereu celui mai nou videoclip'
    ],
    c: 0
  },
  {
    q: 'În era AI, care este rolul principal al artistului-animator?',
    a: [
      'A renunța complet la desenul tradițional',
      'A genera cât mai mult conținut fără selecție',
      'A evita orice instrument digital',
      'Director creativ: AI-ul asistă, dar viziunea și deciziile îi aparțin'
    ],
    c: 3
  }
];

const quizBox = document.getElementById('quiz-box');
let qi = 0, score = 0, answered = false;

function renderQ(){
  answered = false;
  const item = QUIZ[qi];
  quizBox.innerHTML = `
    <div class="term-bar">
      <span class="dot r"></span><span class="dot y"></span><span class="dot g"></span>
      <span class="term-title">quiz_cultura.sh — bash</span>
    </div>
    <div class="term-body">
      <div><span class="cmd">$ quiz --start</span> <span class="ok">[ÎNTREBAREA ${qi+1}/${QUIZ.length}]</span></div>
      <h3 class="q-text">${item.q}</h3>
      <div class="q-answers">
        ${item.a.map((t,i) =>
          `<button type="button" class="q-ans" data-i="${i}">${String.fromCharCode(65+i)}. ${t}</button>`
        ).join('')}
      </div>
      <div class="q-feedback" id="qfb"></div>
      <button type="button" class="q-next" id="qnext" hidden>
        ${qi === QUIZ.length-1 ? 'VEZI REZULTATUL ▸' : 'URMĂTOAREA ▸'}
      </button>
    </div>`;
}

function answer(i){
  if(answered) return;
  answered = true;
  const item = QUIZ[qi];
  const btns = quizBox.querySelectorAll('.q-ans');
  btns.forEach(b => b.disabled = true);
  btns[item.c].classList.add('correct');
  const fb = document.getElementById('qfb');
  if(i === item.c){
    score++;
    fb.textContent = '✔ CORECT. Sistemul approve.';
    fb.className = 'q-feedback good';
  }else{
    btns[i].classList.add('wrong');
    fb.textContent = '✘ GREȘIT — răspunsul corect este marcat mai sus.';
    fb.className = 'q-feedback bad';
  }
  document.getElementById('qnext').hidden = false;
}

function showResult(){
  const pct = Math.round(score / QUIZ.length * 100);
  let rank, msg;
  if(pct === 100){
    rank = 'ARHITECT AL CULTURII INFORMATIONALE';
    msg = 'Scor perfect. Ai stăpânit materia — acum ajută-i și pe ceilalți să învețe.';
  }else if(pct >= 67){
    rank = 'OPERATOR AVANSAT';
    msg = 'Foarte bine! Mai revizuiește secțiunile marcate greșit și ești la maxim.';
  }else if(pct >= 34){
    rank = 'CADET INFORMAȚIONAL';
    msg = 'Bază solidă, dar mai e drum. Recitește MODULE_01 și MODULE_02.';
  }else{
    rank = 'NEOFIT — REIA MATERIALELE';
    msg = 'Fără panică: parcurge secțiunile site-ului și reia testul. Sistemul are răbdare.';
  }
  const filled = Math.round(score / QUIZ.length * 20);
  const bar = '▓'.repeat(filled) + '░'.repeat(20 - filled);
  quizBox.innerHTML = `
    <div class="term-bar">
      <span class="dot r"></span><span class="dot y"></span><span class="dot g"></span>
      <span class="term-title">quiz_cultura.sh — rezultat</span>
    </div>
    <div class="term-body">
      <div><span class="cmd">$ quiz --rezultat</span> <span class="ok">[ANALIZĂ COMPLETĂ]</span></div>
      <p class="res-big">SCOR: ${score}/${QUIZ.length} (${pct}%)</p>
      <div class="res-bar">[${bar}]</div>
      <p class="res-rank">RANG: ${rank}</p>
      <p class="res-msg">${msg}</p>
      <button type="button" class="q-restart">REIA TESTUL ⟲</button>
    </div>`;
}

quizBox.addEventListener('click', e => {
  const ans = e.target.closest('.q-ans');
  if(ans && !answered){ answer(+ans.dataset.i); return; }
  if(e.target.closest('.q-next')){
    qi++;
    qi < QUIZ.length ? renderQ() : showResult();
    return;
  }
  if(e.target.closest('.q-restart')){
    qi = 0; score = 0;
    renderQ();
  }
});

renderQ();
</script>
</body>
</html>
