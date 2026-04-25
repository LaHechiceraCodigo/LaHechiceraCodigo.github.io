---
layout: post
title: "¿Qué es PYTHON?"
Autor: "La Hechicera del Código"
---

Aprende Python desde cero y explora sus capacidades.

{% raw %}
<style>
  #mindmap-universe { 
    min-height: 640px; 
    position: relative; 
    border-radius: 12px; 
    overflow: hidden; 
    font-family: sans-serif;
    background: #080c1f;
  }
  #mindmap-universe * { box-sizing: border-box; margin: 0; padding: 0; }
  canvas#space { position: absolute; inset: 0; width: 100%; height: 100%; z-index: 1; }
  .content { position: relative; z-index: 2; pointer-events: none; }
  .content button, .content .orbit-node, .content .center-node { pointer-events: auto; }
  
  .header { text-align: center; padding: 25px 20px; }
  .header h1 { font-size: 13px; color: #4fc8d4; text-transform: uppercase; letter-spacing: 0.2em; }
  .header p { font-size: 22px; color: #e8f4f8; margin-top: 5px; font-weight: bold; }
  
  .diagram-area { position: relative; width: 100%; height: 420px; }
  .center-node { position: absolute; left: 50%; top: 50%; transform: translate(-50%, -50%); width: 90px; height: 90px; border-radius: 50%; background: radial-gradient(circle, #1a3a6e 0%, #0d1f45 100%); border: 2px solid #4fc8d4; display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; z-index: 10; box-shadow: 0 0 20px rgba(79,200,212,0.4); }
  .center-node span { color: #7de8f0; font-weight: bold; }
  
  .orbit-node { position: absolute; width: 68px; height: 68px; border-radius: 50%; background: radial-gradient(circle, #1a4060 0%, #0d2035 100%); border: 1.5px solid #2a8aaa; display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; z-index: 5; transition: all 0.3s; }
  .orbit-node:hover { transform: scale(1.15); border-color: #4fc8d4; box-shadow: 0 0 15px rgba(79,200,212,0.5); }
  .orbit-node .icon { font-size: 18px; }
  .orbit-node .label { font-size: 8px; color: #4fc8d4; text-align: center; margin-top: 3px; max-width: 55px; line-height: 1.1; }

  .modal-overlay { display: none; position: absolute; inset: 0; background: rgba(5,8,25,0.92); z-index: 100; align-items: center; justify-content: center; }
  .modal-overlay.open { display: flex; }
  .modal { background: #0e1a3d; border: 1.5px solid #4fc8d4; border-radius: 12px; padding: 30px; max-width: 440px; width: 85%; position: relative; color: white; text-align: center; }
  .modal-close { position: absolute; top: 12px; right: 15px; background: none; border: none; color: #4fc8d4; font-size: 22px; cursor: pointer; }
  .modal-tag { display: inline-block; background: rgba(79,200,212,0.1); border: 0.5px solid #4fc8d4; color: #7de8f0; border-radius: 20px; font-size: 10px; padding: 3px 10px; margin: 4px 2px; }
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
      <div class="orbit-node" style="left:calc(50% - 34px); top:10px;" onclick="openNode(0)">
        <span class="icon">🔷</span><span class="label">Objetos</span>
      </div>
      <div class="orbit-node" style="left:calc(50% + 82px); top:44px;" onclick="openNode(1)">
        <span class="icon">🧠</span><span class="label">Alto nivel</span>
      </div>
      <div class="orbit-node" style="left:calc(50% + 132px); top:162px;" onclick="openNode(2)">
        <span class="icon">📦</span><span class="label">Bibliotecas</span>
      </div>
      <div class="orbit-node" style="left:calc(50% - 152px); top:44px;" onclick="openNode(7)">
        <span class="icon">📊</span><span class="label">Análisis</span>
      </div>
    </div>
    <div style="text-align:center; padding-bottom:30px;">
      <button onclick="openCenter()" style="background:rgba(79,200,212,0.1); border:1px solid #4fc8d4; color:#7de8f0; border-radius:20px; padding:10px 20px; cursor:pointer; font-size:11px;">EXPLORAR CARACTERÍSTICAS</button>
    </div>
  </div>

  <div class="modal-overlay" id="modal" onclick="if(event.target==this) closeModal()">
    <div class="modal">
      <button class="modal-close" onclick="closeModal()">✕</button>
      <div id="mIcon" style="font-size:35px; margin-bottom:10px;"></div>
      <h2 id="mTitle" style="color:#7de8f0; margin-bottom:10px; font-size:18px; text-transform: uppercase;"></h2>
      <p id="mBody" style="color:#c0dde8; line-height:1.6; font-size:14px; margin-bottom:15px;"></p>
      <div id="mTags"></div>
    </div>
  </div>
</div>

<script>
const nodes = [
  { icon:"🔷", title:"Orientado a objetos", body:"Python organiza el código en clases y objetos para modelar la realidad.", tags:["Clases","Herencia"] },
  { icon:"🧠", title:"Alto nivel", body:"Sintaxis amigable y cercana al lenguaje humano.", tags:["Legibilidad","Abstracción"] },
  { icon:"📦", title:"Bibliotecas", body:"Ecosistema enorme como Pandas y NumPy para ciencia de datos.", tags:["Pandas","NumPy"] },
  { icon:"🌐", title:"Escalable", body:"Funciona igual en Windows, Mac o Linux.", tags:["Portable"] },
  { icon:"🤝", title:"Colaborativo", body:"Es código abierto y gratuito para todo el mundo.", tags:["Open Source"] },
  { icon:"🌱", title:"Fácil de aprender", body:"Ideal para personas que inician en la programación.", tags:["Sintaxis clara"] },
  { icon:"🔍", title:"Web Scraping", body:"Extrae datos de páginas web automáticamente.", tags:["BeautifulSoup"] },
  { icon:"📊", title:"Análisis de datos", body:"Estándar de la industria para procesar información.", tags:["Data Science"] }
];

function openNode(i) {
  const n = nodes[i];
  document.getElementById('mIcon').textContent = n.icon;
  document.getElementById('mTitle').textContent = n.title;
  document.getElementById('mBody').textContent = n.body;
  document.getElementById('mTags').innerHTML = n.tags.map(function(t){ 
    return '<span class="modal-tag">' + t + '</span>'; 
  }).join('');
  document.getElementById('modal').classList.add('open');
}

function openCenter() {
  document.getElementById('mIcon').textContent = '🐍';
  document.getElementById('mTitle').textContent = '¿Qué es Python?';
  document.getElementById('mBody').textContent = 'Es un lenguaje interpretado, de alto nivel y el más usado en IA y ciencia de datos.';
  document.getElementById('mTags').innerHTML = '';
  document.getElementById('modal').classList.add('open');
}

function closeModal() { document.getElementById('modal').classList.remove('open'); }

// --- MOTOR ESPACIAL CON ESTRELLAS FUGACES ---
const canvas = document.getElementById('space');
const ctx = canvas.getContext('2d');
let W, H, stars = [], shootingStars = [];

function resize() {
  W = canvas.width = canvas.parentElement.offsetWidth;
  H = canvas.height = canvas.parentElement.offsetHeight;
}

function initStars() {
  stars = [];
  for(let i=0; i<100; i++) {
    stars.push({ x: Math.random()*W, y: Math.random()*H, r: Math.random()*1.2, p: Math.random()*Math.PI*2, s: 0.02+Math.random()*0.03 });
  }
}

function spawnShootingStar() {
  shootingStars.push({
    x: Math.random()*W, y: Math.random()*H*0.5,
    vx: 4+Math.random()*4, vy: 2+Math.random()*2,
    len: 50+Math.random()*50, alpha: 1
  });
}

function draw(ts) {
  ctx.fillStyle = "#080c1f";
  ctx.fillRect(0,0,W,H);
  
  // Estrellas fijas parpadeantes
  stars.forEach(s => {
    let opacity = 0.3 + Math.abs(Math.sin(ts*0.001*s.s + s.p))*0.7;
    ctx.beginPath();
    ctx.arc(s.x, s.y, s.r, 0, Math.PI*2);
    ctx.fillStyle = "rgba(255, 255, 255, " + opacity + ")";
    ctx.fill();
  });

  // Estrellas fugaces cada 4 segundos aprox
  if(Math.random() < 0.005) spawnShootingStar();

  shootingStars = shootingStars.filter(ss => ss.alpha > 0);
  shootingStars.forEach(ss => {
    ctx.beginPath();
    let grad = ctx.createLinearGradient(ss.x, ss.y, ss.x-ss.vx*10, ss.y-ss.vy*10);
    grad.addColorStop(0, "rgba(255,255,255," + ss.alpha + ")");
    grad.addColorStop(1, "rgba(255,255,255,0)");
    ctx.strokeStyle = grad;
    ctx.lineWidth = 2;
    ctx.moveTo(ss.x, ss.y);
    ctx.lineTo(ss.x - ss.vx*3, ss.y - ss.vy*3);
    ctx.stroke();
    ss.x += ss.vx; ss.y += ss.vy; ss.alpha -= 0.01;
  });

  requestAnimationFrame(draw);
}

window.addEventListener('resize', () => { resize(); initStars(); });
resize(); initStars(); draw(0);
</script>
{% endraw %}
