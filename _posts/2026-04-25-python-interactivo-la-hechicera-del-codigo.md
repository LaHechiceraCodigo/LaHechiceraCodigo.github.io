---
layout: post
title: "¿Qué es PYTHON?"
---

Aprende Python desde cero...

{% raw %}
<style>
  /* Pega aquí todo el código que te pasé antes */
</style>

<div id="mindmap-app">
  </div>

{% raw %}
<script>
  /* Todo el JavaScript */
</script>


<style>
  /* Reseteo encapsulado solo para este componente */
  #mindmap-app, #mindmap-app * { box-sizing: border-box; margin: 0; padding: 0; }
  
  #mindmap-app { min-height: 640px; position: relative; border-radius: 12px; overflow: hidden; font-family: sans-serif; background-color: #080c1f; }
  #mindmap-app canvas#space { position: absolute; inset: 0; width: 100%; height: 100%; border-radius: 12px; }
  #mindmap-app .content { position: relative; z-index: 2; }
  #mindmap-app .header { text-align: center; padding: 28px 20px 12px; }
  #mindmap-app .header h1 { font-size: 13px; font-weight: 500; letter-spacing: 0.2em; color: #4fc8d4; text-transform: uppercase; }
  #mindmap-app .header p { font-size: 22px; font-weight: 500; color: #e8f4f8; margin-top: 4px; }
  #mindmap-app .diagram-area { position: relative; width: 100%; height: 420px; }
  #mindmap-app svg.connections { position: absolute; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; }
  #mindmap-app .center-node { position: absolute; left: 50%; top: 50%; transform: translate(-50%, -50%); width: 90px; height: 90px; border-radius: 50%; background: radial-gradient(circle, #1a3a6e 0%, #0d1f45 100%); border: 2px solid #4fc8d4; display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; z-index: 10; box-shadow: 0 0 24px rgba(79,200,212,0.35); transition: box-shadow 0.3s; }
  #mindmap-app .center-node:hover { box-shadow: 0 0 36px rgba(79,200,212,0.6); }
  #mindmap-app .center-node span { font-size: 15px; font-weight: 500; color: #7de8f0; letter-spacing: 0.12em; }
  #mindmap-app .center-node small { font-size: 9px; color: #4fc8d4; letter-spacing: 0.08em; margin-top: 2px; }
  #mindmap-app .orbit-node { position: absolute; width: 68px; height: 68px; border-radius: 50%; background: radial-gradient(circle, #1a4060 0%, #0d2035 100%); border: 1.5px solid #2a8aaa; display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; transition: transform 0.2s, border-color 0.2s, box-shadow 0.2s; z-index: 5; }
  #mindmap-app .orbit-node:hover { transform: scale(1.15); border-color: #4fc8d4; box-shadow: 0 0 18px rgba(79,200,212,0.5); }
  #mindmap-app .orbit-node .icon { font-size: 18px; }
  #mindmap-app .orbit-node .label { font-size: 8px; color: #4fc8d4; text-align: center; margin-top: 3px; letter-spacing: 0.04em; line-height: 1.2; max-width: 60px; }
  #mindmap-app .modal-overlay { display: none; position: absolute; inset: 0; background: rgba(5,8,25,0.88); z-index: 50; align-items: center; justify-content: center; border-radius: 12px; }
  #mindmap-app .modal-overlay.open { display: flex; }
  #mindmap-app .modal { background: linear-gradient(145deg, #0e1a3d, #081228); border: 1.5px solid #4fc8d4; border-radius: 12px; padding: 28px; max-width: 460px; width: 90%; position: relative; }
  #mindmap-app .modal-close { position: absolute; top: 12px; right: 16px; background: none; border: none; color: #4fc8d4; font-size: 20px; cursor: pointer; }
  #mindmap-app .modal-icon { font-size: 36px; text-align: center; margin-bottom: 8px; }
  #mindmap-app .modal-title { font-size: 16px; font-weight: 500; color: #7de8f0; text-align: center; letter-spacing: 0.1em; text-transform: uppercase; margin-bottom: 4px; }
  #mindmap-app .modal-subtitle { font-size: 11px; color: #4fc8d4; text-align: center; letter-spacing: 0.08em; margin-bottom: 16px; }
  #mindmap-app .modal-divider { border: none; border-top: 0.5px solid #2a5a7a; margin: 12px 0; }
  #mindmap-app .modal-body { font-size: 13px; color: #c0dde8; line-height: 1.7; }
  #mindmap-app .modal-tag { display: inline-block; background: rgba(79,200,212,0.12); border: 0.5px solid #4fc8d4; color: #7de8f0; border-radius: 20px; font-size: 10px; padding: 3px 10px; margin: 4px 3px 0; letter-spacing: 0.05em; }
  #mindmap-app .permite-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-top: 14px; }
  #mindmap-app .permite-card { background: rgba(79,200,212,0.06); border: 0.5px solid #2a5a7a; border-radius: 8px; padding: 12px 10px; text-align: center; cursor: pointer; transition: border-color 0.2s; }
  #mindmap-app .permite-card:hover { border-color: #4fc8d4; }
  #mindmap-app .permite-card .p-icon { font-size: 22px; margin-bottom: 5px; }
  #mindmap-app .permite-card .p-title { font-size: 10px; color: #7de8f0; letter-spacing: 0.05em; font-weight: 500; }
  #mindmap-app .footer-hint { text-align: center; padding: 0 20px 20px; }
  #mindmap-app .footer-hint p { font-size: 11px; color: #4fc8d4; letter-spacing: 0.08em; }
  #mindmap-app .footer-hint button { margin-top: 10px; background: rgba(79,200,212,0.1); border: 1px solid #4fc8d4; color: #7de8f0; border-radius: 20px; padding: 7px 20px; font-size: 11px; cursor: pointer; letter-spacing: 0.08em; transition: background 0.2s; }
  #mindmap-app .footer-hint button:hover { background: rgba(79,200,212,0.2); }
</style>

{% endraw %}
<div id="mindmap-app">
  <canvas id="space"></canvas>

  <div class="content">
    <div class="header">
      <h1>Programación con</h1>
      <p>Python para el análisis de datos</p>
    </div>

    <div class="diagram-area" id="diagram">
      <svg class="connections" id="svgLines"></svg>
      <div class="center-node" onclick="openCenter()">
        <span>PYTHON</span>
        <small>¿QUÉ ES?</small>
      </div>
      <div class="orbit-node" id="n0" style="left:calc(50% - 34px);top:10px;" onclick="openNode(0)">
        <span class="icon">🔷</span><span class="label">Orientado a objetos</span>
      </div>
      <div class="orbit-node" id="n1" style="left:calc(50% + 82px);top:44px;" onclick="openNode(1)">
        <span class="icon">🧠</span><span class="label">Alto nivel</span>
      </div>
      <div class="orbit-node" id="n2" style="left:calc(50% + 132px);top:162px;" onclick="openNode(2)">
        <span class="icon">📦</span><span class="label">Bibliotecas</span>
      </div>
      <div class="orbit-node" id="n3" style="left:calc(50% + 82px);top:290px;" onclick="openNode(3)">
        <span class="icon">🌐</span><span class="label">Escalable y portable</span>
      </div>
      <div class="orbit-node" id="n4" style="left:calc(50% - 34px);top:338px;" onclick="openNode(4)">
        <span class="icon">🤝</span><span class="label">Gratuito y colaborativo</span>
      </div>
      <div class="orbit-node" id="n5" style="left:calc(50% - 152px);top:290px;" onclick="openNode(5)">
        <span class="icon">🌱</span><span class="label">Fácil de aprender</span>
      </div>
      <div class="orbit-node" id="n6" style="left:calc(50% - 202px);top:162px;" onclick="openNode(6)">
        <span class="icon">🔍</span><span class="label">Web Scraping</span>
      </div>
      <div class="orbit-node" id="n7" style="left:calc(50% - 152px);top:44px;" onclick="openNode(7)">
        <span class="icon">📊</span><span class="label">Análisis de datos</span>
      </div>
    </div>

    <div class="footer-hint">
      <p>HAZ CLIC EN CUALQUIER NODO PARA EXPLORAR</p>
      <button onclick="openPermite()">▸ VER PYTHON PERMITE...</button>
    </div>
  </div>

  <div class="modal-overlay" id="modal">
    <div class="modal">
      <button class="modal-close" onclick="closeModal()">✕</button>
      <div class="modal-icon" id="mIcon"></div>
      <div class="modal-title" id="mTitle"></div>
      <div class="modal-subtitle" id="mSubtitle"></div>
      <hr class="modal-divider">
      <div class="modal-body" id="mBody"></div>
    </div>
  </div>
</div>

<script>
const nodes = [
  { icon:"🔷", title:"Orientado a objetos", subtitle:"Característica · Python A", body:`Python organiza el código en <strong style="color:#7de8f0">clases y objetos</strong>, permitiendo reutilizar código, estructurarlo de forma lógica y modelar situaciones del mundo real con claridad.`, tags:["Clases","Objetos","Herencia","Encapsulamiento"] },
  { icon:"🧠", title:"Alto nivel", subtitle:"Característica · Python B", body:`Su sintaxis se parece al lenguaje humano. No gestionas memoria manualmente — Python lo hace por ti, permitiéndote concentrarte en <strong style="color:#7de8f0">resolver problemas</strong>.`, tags:["Sintaxis natural","Legibilidad","Abstracción"] },
  { icon:"📦", title:"Gran cantidad de bibliotecas", subtitle:"Característica · Python C", body:`Ecosistema enorme de <strong style="color:#7de8f0">bibliotecas especializadas</strong>: NumPy (álgebra lineal), Pandas (tablas de datos) y Scikit-Learn (machine learning). Gran versatilidad en ciencia de datos.`, tags:["NumPy","Pandas","Scikit-Learn","Matplotlib","TensorFlow"] },
  { icon:"🌐", title:"Escalabilidad y portabilidad", subtitle:"Característica · Python D", body:`Python es <strong style="color:#7de8f0">multiplataforma</strong>: el mismo código corre en Windows, macOS y Linux. Proyectos pequeños pueden crecer hacia sistemas de gran escala sin cambiar de lenguaje.`, tags:["Windows","macOS","Linux","Multiplataforma"] },
  { icon:"🤝", title:"Gratuito y colaborativo", subtitle:"Característica · Python E", body:`Python es <strong style="color:#7de8f0">código abierto</strong> y completamente gratuito. Su comunidad global contribuye constantemente con nuevas herramientas, correcciones y mejoras.`, tags:["Open Source","Comunidad","Gratuito","CPython"] },
  { icon:"🌱", title:"Fácil de aprender", subtitle:"Característica · Python F", body:`Curva de aprendizaje amigable con <strong style="color:#7de8f0">sintaxis clara y concisa</strong>. Los principiantes pueden escribir programas funcionales desde los primeros días. El lenguaje más recomendado para iniciar en programación.`, tags:["Principiantes","Sintaxis clara","Rápido de aprender"] },
  { icon:"🔍", title:"Web Scraping", subtitle:"Python permite · Aplicación 1", body:`Extrae datos de páginas web de forma automática. Herramientas como <strong style="color:#7de8f0">BeautifulSoup y Scrapy</strong> capturan información para analizarla o almacenarla.`, tags:["BeautifulSoup","Scrapy","Requests","Selenium"] },
  { icon:"📊", title:"Análisis de datos y visualización", subtitle:"Python permite · Aplicación 2", body:`Estándar de la industria para el <strong style="color:#7de8f0">análisis de datos</strong>. Pandas manipula tablas, NumPy realiza cálculos y Matplotlib/Seaborn crean visualizaciones poderosas.`, tags:["Pandas","NumPy","Matplotlib","Seaborn"] }
];

const permiteNodes = [
  { icon:"🌍", title:"Aplicaciones Web", body:"Construye apps web con Django o Flask, desde sitios simples hasta plataformas complejas con bases de datos.", tags:["Django","Flask","FastAPI"] },
  { icon:"📊", title:"Análisis de datos", body:"Analiza y visualiza datos con Pandas, NumPy y Matplotlib para extraer insights valiosos.", tags:["Pandas","NumPy","Matplotlib"] },
  { icon:"🔍", title:"Web Scraping", body:"Captura datos de páginas web automáticamente para alimentar tus análisis o bases de datos.", tags:["BeautifulSoup","Scrapy"] },
  { icon:"🎮", title:"Videojuegos", body:"Crea videojuegos 2D con Pygame o prototipos para aprender lógica de programación.", tags:["Pygame","Arcade"] },
  { icon:"🖥️", title:"Apps de escritorio", body:"Desarrolla interfaces gráficas para Windows, macOS y Linux con Tkinter o PyQt.", tags:["Tkinter","PyQt","Kivy"] }
];

function openNode(i) {
  const n = nodes[i];
  document.getElementById('mIcon').textContent = n.icon;
  document.getElementById('mTitle').textContent = n.title;
  document.getElementById('mSubtitle').textContent = n.subtitle;
  document.getElementById('mBody').innerHTML = n.body + '<div style="margin-top:12px">' + n.tags.map(t=>`<span class="modal-tag">\${t}</span>`).join('') + '</div>';
  document.getElementById('modal').classList.add('open');
}
function openCenter() {
  document.getElementById('mIcon').textContent = '🐍';
  document.getElementById('mTitle').textContent = '¿Qué es Python?';
  document.getElementById('mSubtitle').textContent = 'Lenguaje de programación de propósito general';
  document.getElementById('mBody').innerHTML = `Python es un lenguaje <strong style="color:#7de8f0">interpretado, de alto nivel y propósito general</strong>, creado por Guido van Rossum en 1991. Su filosofía prioriza la legibilidad del código y la productividad.<br><br>Es el lenguaje más popular en ciencia de datos e inteligencia artificial. <strong style="color:#7de8f0">Haz clic en los nodos</strong> para explorar sus características.`;
  document.getElementById('modal').classList.add('open');
}
function openPermite() {
  document.getElementById('mIcon').textContent = '⚡';
  document.getElementById('mTitle').textContent = 'Python permite...';
  document.getElementById('mSubtitle').textContent = 'Aplicaciones y casos de uso';
  let html = '<div class="permite-grid">';
  permiteNodes.forEach((p,i) => { html += `<div class="permite-card" onclick="openPermiteDetail(\${i})"><div class="p-icon">\${p.icon}</div><div class="p-title">\${p.title}</div></div>`; });
  html += '</div>';
  document.getElementById('mBody').innerHTML = html;
  document.getElementById('modal').classList.add('open');
}
function openPermiteDetail(i) {
  const p = permiteNodes[i];
  document.getElementById('mIcon').textContent = p.icon;
  document.getElementById('mTitle').textContent = p.title;
  document.getElementById('mSubtitle').textContent = 'Python permite · Explorar';
  document.getElementById('mBody').innerHTML = p.body + '<div style="margin-top:12px">' + p.tags.map(t=>`<span class="modal-tag">\${t}</span>`).join('') + '</div><div style="margin-top:16px"><button onclick="openPermite()" style="background:rgba(79,200,212,0.1);border:0.5px solid #4fc8d4;color:#7de8f0;border-radius:16px;padding:5px 14px;font-size:11px;cursor:pointer;">← Volver</button></div>';
}
function closeModal() { document.getElementById('modal').classList.remove('open'); }
document.getElementById('modal').addEventListener('click', function(e){ if(e.target===this) closeModal(); });

function drawLines() {
  const svg = document.getElementById('svgLines');
  const area = document.getElementById('diagram');
  const W = area.offsetWidth, H = area.offsetHeight;
  const cx = W/2, cy = H/2;
  svg.setAttribute('viewBox',`0 0 \${W} \${H}`);
  const ids = ['n0','n1','n2','n3','n4','n5','n6','n7'];
  let lines = '';
  ids.forEach(id => {
    const el = document.getElementById(id);
    if (!el) return;
    const nx = el.offsetLeft + 34, ny = el.offsetTop + 34;
    lines += `<line x1="\${cx}" y1="\${cy}" x2="\${nx}" y2="\${ny}" stroke="#2a5a7a" stroke-width="1" stroke-dasharray="4 3" opacity="0.7"/>`;
  });
  svg.innerHTML = lines;
}

// ── SPACE CANVAS ──────────────────────────────────────────────
const canvas = document.getElementById('space');
const ctx = canvas.getContext('2d');

let W, H, stars = [], nebulae = [], shootingStars = [];

function resize() {
  const app = document.getElementById('mindmap-app');
  W = canvas.width = app.offsetWidth;
  H = canvas.height = app.offsetHeight;
}

function initStars() {
  stars = [];
  for (let i = 0; i < 180; i++) {
    stars.push({
      x: Math.random() * W,
      y: Math.random() * H,
      r: Math.random() * 1.4 + 0.3,
      base: Math.random() * 0.5 + 0.2,
      speed: Math.random() * 0.008 + 0.002,
      phase: Math.random() * Math.PI * 2,
      color: Math.random() > 0.85 ? '#b0d8ff' : Math.random() > 0.6 ? '#e0eeff' : '#ffffff'
    });
  }
}

function initNebulae() {
  nebulae = [
    { x: W*0.15, y: H*0.25, rx: W*0.22, ry: H*0.22, color: 'rgba(80,20,140,0.13)' },
    { x: W*0.82, y: H*0.65, rx: W*0.25, ry: H*0.2,  color: 'rgba(10,60,160,0.12)' },
    { x: W*0.5,  y: H*0.8,  rx: W*0.3,  ry: H*0.15, color: 'rgba(0,120,100,0.08)' },
    { x: W*0.7,  y: H*0.1,  rx: W*0.2,  ry: H*0.18, color: 'rgba(60,0,120,0.1)'  }
  ];
}

function spawnShootingStar() {
  const angle = Math.PI/6 + Math.random()*Math.PI/8;
  const startX = Math.random() * W * 0.7;
  const startY = Math.random() * H * 0.4;
  const length = 120 + Math.random() * 100;
  const speed = 6 + Math.random() * 5;
  shootingStars.push({
    x: startX, y: startY,
    vx: Math.cos(angle) * speed,
    vy: Math.sin(angle) * speed,
    length, alpha: 1,
    trail: [], maxTrail: Math.floor(length / speed) + 4
  });
}

let lastShooting = 0;
const SHOOTING_INTERVAL = 5000 + Math.random() * 4000;
let nextShooting = SHOOTING_INTERVAL;

function drawFrame(ts) {
  ctx.clearRect(0, 0, W, H);

  const bg = ctx.createLinearGradient(0, 0, W, H);
  bg.addColorStop(0,   '#080c1f');
  bg.addColorStop(0.4, '#0d1535');
  bg.addColorStop(0.7, '#120826');
  bg.addColorStop(1,   '#0a0620');
  ctx.fillStyle = bg;
  ctx.fillRect(0, 0, W, H);

  nebulae.forEach(n => {
    const g = ctx.createRadialGradient(n.x, n.y, 0, n.x, n.y, Math.max(n.rx, n.ry));
    g.addColorStop(0, n.color);
    g.addColorStop(1, 'rgba(0,0,0,0)');
    ctx.save();
    ctx.scale(n.rx / Math.max(n.rx,n.ry
