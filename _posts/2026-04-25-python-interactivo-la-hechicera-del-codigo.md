---
layout: post
title: "¿Qué es PYTHON?"
---

Aprende Python desde cero y explora sus capacidades.

{% raw %}
<style>
  #mindmap-universe { 
    min-height: 640px; position: relative; border-radius: 12px; 
    overflow: hidden; font-family: sans-serif; background: #080c1f;
  }
  canvas#space { position: absolute; inset: 0; width: 100%; height: 100%; z-index: 1; }
  .content { position: relative; z-index: 2; pointer-events: none; text-align: center; }
  .content button, .content .orbit-node, .content .center-node { pointer-events: auto; }
  
  .header { padding: 25px 20px; }
  .header h1 { font-size: 13px; color: #4fc8d4; text-transform: uppercase; letter-spacing: 0.2em; }
  .header p { font-size: 22px; color: #e8f4f8; margin-top: 5px; font-weight: bold; }
  
  .diagram-area { position: relative; width: 100%; height: 420px; margin: 0 auto; }
  .center-node { position: absolute; left: 50%; top: 50%; transform: translate(-50%, -50%); width: 90px; height: 90px; border-radius: 50%; background: #0d1f45; border: 2px solid #4fc8d4; display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; z-index: 10; box-shadow: 0 0 20px rgba(79,200,212,0.4); }
  .center-node span { color: #7de8f0; font-weight: bold; font-size: 14px; }
  
  .orbit-node { position: absolute; width: 68px; height: 68px; border-radius: 50%; background: #0d2035; border: 1.5px solid #2a8aaa; display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; z-index: 5; transition: transform 0.2s; }
  .orbit-node:hover { transform: scale(1.1); border-color: #4fc8d4; }
  .orbit-node .icon { font-size: 18px; }
  .orbit-node .label { font-size: 8px; color: #4fc8d4; margin-top: 3px; max-width: 55px; line-height: 1.1; }

  .modal-overlay { display: none; position: absolute; inset: 0; background: rgba(5,8,25,0.92); z-index: 100; align-items: center; justify-content: center; }
  .modal-overlay.open { display: flex; }
  .modal { background: #0e1a3d; border: 1.5px solid #4fc8d4; border-radius: 12px; padding: 25px; max-width: 440px; width: 90%; position: relative; color: white; }
  .modal-close { position: absolute; top: 10px; right: 15px; background: none; border: none; color: #4fc8d4; font-size: 22px; cursor: pointer; }
  
  .permite-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 15px; }
  .permite-card { background: rgba(79,200,212,0.1); border: 1px solid #2a5a7a; border-radius: 8px; padding: 10px; cursor: pointer; }
  .modal-tag { display: inline-block; background: rgba(79,200,212,0.1); border: 0.5px solid #4fc8d4; color: #7de8f0; border-radius: 15px; font-size: 9px; padding: 2px 8px; margin: 2px; }
</style>

<div id="mindmap-universe">
  <canvas id="space"></canvas>
  <div class="content">
    <div class="header">
      <h1>Programación con</h1>
      <p>Python para el análisis de datos</p>
    </div>
    <div class="diagram-area">
      <div class="center-node" onclick="openCenter()">
        <span>PYTHON</span>
        <small style="color:#4fc8d4; font-size:9px">¿QUÉ ES?</small>
      </div>
      <div class="orbit-node" style="left:calc(50% - 34px); top:10px;" onclick="openNode(0)"><span class="icon">🔷</span><span class="label">Objetos</span></div>
      <div class="orbit-node" style="left:calc(50% + 82px); top:44px;" onclick="openNode(1)"><span class="icon">🧠</span><span class="label">Alto nivel</span></div>
      <div class="orbit-node" style="left:calc(50% + 132px); top:162px;" onclick="openNode(2)"><span class="icon">📦</span><span class="label">Bibliotecas</span></div>
      <div class="orbit-node" style="left:calc(50% + 82px); top:290px;" onclick="openNode(3)"><span class="icon">🌐</span><span class="label">Escalable</span></div>
      <div class="orbit-node" style="left:calc(50% - 34px); top:338px;" onclick="openNode(4)"><span class="icon">🤝</span><span class="label">Gratuito</span></div>
      <div class="orbit-node" style="left:calc(50% - 152px); top:290px;" onclick="openNode(5)"><span class="icon">🌱</span><span class="label">Fácil</span></div>
      <div class="orbit-node" style="left:calc(50% - 202px); top:162px;" onclick="openNode(6)"><span class="icon">🔍</span><span class="label">Scraping</span></div>
      <div class="orbit-node" style="left:calc(50% - 152px); top:44px;" onclick="openNode(7)"><span class="icon">📊</span><span class="label">Análisis</span></div>
    </div>
    <div style="padding-bottom:20px;">
      <button onclick="openPermite()" style="background:rgba(79,200,212,0.1); border:1px solid #4fc8d4; color:#7de8f0; border-radius:20px; padding:8px 15px; cursor:pointer; font-size:11px;">▸ VER PYTHON PERMITE...</button>
    </div>
  </div>

  <div class="modal-overlay" id="modal" onclick="if(event.target==this) closeModal()">
    <div class="modal">
      <button class="modal-close" onclick="closeModal()">✕</button>
      <div id="mIcon" style="font-size:30px; margin-bottom:10px;"></div>
      <h2 id="mTitle" style="color:#7de8f0; margin-bottom:8px; font-size:18px;"></h2>
      <div id="mBody" style="color:#c0dde8; font-size:13px; line-height:1.5;"></div>
    </div>
  </div>
</div>

<script>
const nodes = [
  { i:"🔷", t:"Orientado a objetos", b:"Organiza código en clases y objetos para reutilizarlo.", tags:["Clases","Objetos"] },
  { i:"🧠", t:"Alto nivel", b:"Sintaxis cercana al lenguaje humano, Python gestiona la memoria por ti.", tags:["Sintaxis","Legibilidad"] },
  { i:"📦", t:"Bibliotecas", b:"Enorme ecosistema: NumPy, Pandas y Scikit-Learn.", tags:["Pandas","NumPy"] },
  { i:"🌐", t:"Escalable", b:"Multiplataforma: funciona en Windows, Mac y Linux.", tags:["Portable"] },
  { i:"🤝", t:"Gratuito", b:"Código abierto y comunidad global activa.", tags:["Open Source"] },
  { i:"🌱", t:"Fácil de aprender", b:"Sintaxis clara, ideal para principiantes.", tags:["Sencillo"] },
  { i:"🔍", t:"Web Scraping", b:"Extrae datos de sitios web con BeautifulSoup.", tags:["Scrapy"] },
  { i:"📊", t:"Análisis de datos", b:"Estándar para procesar y visualizar información.", tags:["Data Science"] }
];

const permite = [
  { i:"🌍", t:"Apps Web", b:"Django y Flask." },
  { i:"📊", t:"Ciencia de Datos", b:"Análisis avanzado." },
  { i:"🔍", t:"Automatización", b:"Tareas repetitivas." },
  { i:"🎮", t:"Videojuegos", b:"Pygame y lógica." }
];

function openNode(idx) {
  const n = nodes[idx];
  showModal(n.i, n.t, n.b, n.tags);
}

function openCenter() {
  showModal('🐍', '¿Qué es Python?', 'Un lenguaje versátil creado para ser leído y compartido.', []);
}

function openPermite() {
  let html = '<div class="permite-grid">';
  permite.forEach(p => {
    html += '<div class="permite-card"><b>' + p.i + ' ' + p.t + '</b><br><small>' + p.b + '</small></div>';
  });
  html += '</div>';
  showModal('⚡', 'Python permite...', html, null);
}

function showModal(icon, title, body, tags) {
  document.getElementById('mIcon').textContent = icon;
  document.getElementById('mTitle').textContent = title;
  let content = body;
  if(tags) {
    content += '<div style="margin-top:10px">' + tags.map(t => '<span class="modal-tag">' + t + '</span>').join('') + '</div>';
  }
  document.getElementById('mBody').innerHTML = content;
  document.getElementById('modal').classList.add('open');
}

function closeModal() { document.getElementById('modal').classList.remove('open'); }

// --- ANIMACIÓN DE ESPACIO SEGURA ---
const canvas = document.getElementById('space');
const ctx = canvas.getContext('2d');
let W, H, stars = [], shootingStars = [];

function init() {
  W = canvas.width = canvas.parentElement.offsetWidth;
  H = canvas.height = canvas.parentElement.offsetHeight;
  stars = [];
  for(let i=0; i<150; i++) {
    stars.push({ x: Math.random()*W, y: Math.random()*H, r: Math.random()*1.2, o: Math.random(), s: 0.01+Math.random()*0.02 });
  }
}

function spawnShooting() {
  shootingStars.push({ x: Math.random()*W, y: Math.random()*H*0.5, vx: 5, vy: 3, a: 1 });
}

function draw() {
  ctx.fillStyle = "#080c1f";
  ctx.fillRect(0,0,W,H);
  
  stars.forEach(s => {
    s.o += s.s;
    if(s.o > 1 || s.o < 0) s.s *= -1;
    ctx.beginPath();
    ctx.arc(s.x, s.y, s.r, 0, Math.PI*2);
    ctx.fillStyle = "rgba(255,255,255," + Math.abs(s.o) + ")";
    ctx.fill();
  });

  if(Math.random() < 0.005) spawnShooting();
  
  shootingStars = shootingStars.filter(ss => ss.a > 0);
  shootingStars.forEach(ss => {
    ctx.beginPath();
    ctx.moveTo(ss.x, ss.y);
    ctx.lineTo(ss.x - 40, ss.y - 24);
    ctx.strokeStyle = "rgba(255,255,255," + ss.a + ")";
    ctx.stroke();
    ss.x += ss.vx; ss.y += ss.vy; ss.a -= 0.02;
  });
  requestAnimationFrame(draw);
}

window.addEventListener('resize', init);
init(); draw();
</script>
{% endraw %}
