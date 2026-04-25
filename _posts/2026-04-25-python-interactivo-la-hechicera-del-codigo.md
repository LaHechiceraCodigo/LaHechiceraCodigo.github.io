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
  .center-node { position: absolute; left: 50%; top: 50%; transform: translate(-50%, -50%); width: 90px; height: 90px; border-radius: 50%; background: #0d1f45; border: 2px solid #4fc8d4; display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; z-index: 10; box-shadow: 0 0 20px rgba(79,200,212,0.4); }
  .center-node span { color: #7de8f0; font-weight: bold; }
  
  .orbit-node { position: absolute; width: 68px; height: 68px; border-radius: 50%; background: #0d2035; border: 1.5px solid #2a8aaa; display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; z-index: 5; transition: transform 0.2s; }
  .orbit-node:hover { transform: scale(1.1); border-color: #4fc8d4; }
  .orbit-node .icon { font-size: 18px; }
  .orbit-node .label { font-size: 8px; color: #4fc8d4; text-align: center; margin-top: 3px; max-width: 55px; line-height: 1.1; }

  .modal-overlay { display: none; position: absolute; inset: 0; background: rgba(5,8,25,0.92); z-index: 100; align-items: center; justify-content: center; }
  .modal-overlay.open { display: flex; }
  .modal { background: #0e1a3d; border: 1.5px solid #4fc8d4; border-radius: 12px; padding: 30px; max-width: 420px; width: 85%; position: relative; color: white; text-align: center; }
  .modal-close { position: absolute; top: 12px; right: 15px; background: none; border: none; color: #4fc8d4; font-size: 22px; cursor: pointer; }
</style>

<div id="mindmap-universe">
  <canvas id="space"></canvas>
  <div class="content">
    <div class="header">
      <h1>Programación con</h1>
      <p>Python para el análisis de datos</p>
    </div>
    <div class="diagram-area">
      <div class="center-node" onclick="openNode(-1)">
        <span>PYTHON</span>
        <small style="color:#4fc8d4; font-size:9px">¿QUÉ ES?</small>
      </div>
      <div class="orbit-node" style="left:calc(50% - 34px); top:10px;" onclick="openNode(0)">
        <span class="icon">🔷</span><span class="label">Orientado a Objetos</span>
      </div>
      <div class="orbit-node" style="left:calc(50% + 100px); top:160px;" onclick="openNode(1)">
        <span class="icon">🧠</span><span class="label">Alto nivel</span>
      </div>
      <div class="orbit-node" style="left:calc(50% - 168px); top:160px;" onclick="openNode(2)">
        <span class="icon">📊</span><span class="label">Análisis de Datos</span>
      </div>
    </div>
    <div style="text-align:center; padding-bottom:30px;">
      <button onclick="openNode(-1)" style="background:rgba(79,200,212,0.1); border:1px solid #4fc8d4; color:#7de8f0; border-radius:20px; padding:10px 20px; cursor:pointer; font-size:11px;">EXPLORAR CONJURO</button>
    </div>
  </div>

  <div class="modal-overlay" id="modal" onclick="if(event.target==this) closeModal()">
    <div class="modal">
      <button class="modal-close" onclick="closeModal()">✕</button>
      <div id="mIcon" style="font-size:35px; margin-bottom:10px;"></div>
      <h2 id="mTitle" style="color:#7de8f0; margin-bottom:10px; font-size:18px;"></h2>
      <p id="mBody" style="color:#c0dde8; line-height:1.6; font-size:14px;"></p>
    </div>
  </div>
</div>

<script>
const info = [
  { i:"🔷", t:"Orientado a Objetos", b:"Python permite organizar código en clases para reutilizarlo y hacerlo más lógico." },
  { i:"🧠", t:"Alto Nivel", b:"Su lenguaje es muy parecido al humano, facilitando la lectura y escritura." },
  { i:"📊", t:"Análisis de Datos", b:"Es la herramienta líder para procesar grandes volúmenes de información y crear visualizaciones." }
];

function openNode(id) {
  const m = document.getElementById('modal');
  const icon = document.getElementById('mIcon');
  const title = document.getElementById('mTitle');
  const body = document.getElementById('mBody');
  
  if(id === -1) {
    icon.textContent = "🐍";
    title.textContent = "¿Qué es Python?";
    body.textContent = "Un lenguaje potente, versátil y el favorito de la Hechicera para dominar el mundo de los datos.";
  } else {
    icon.textContent = info[id].i;
    title.textContent = info[id].t;
    body.textContent = info[id].b;
  }
  m.classList.add('open');
}

function closeModal() { document.getElementById('modal').classList.remove('open'); }

// --- ANIMACIÓN ESPACIAL SEGURA PARA JEKYLL ---
const canvas = document.getElementById('space');
const ctx = canvas.getContext('2d');
let stars = [];

function init() {
  canvas.width = canvas.parentElement.offsetWidth;
  canvas.height = canvas.parentElement.offsetHeight;
  stars = [];
  for(let i=0; i<150; i++) {
    stars.push({
      x: Math.random() * canvas.width,
      y: Math.random() * canvas.height,
      size: Math.random() * 1.5,
      opacity: Math.random(),
      speed: 0.01 + Math.random() * 0.02
    });
  }
}

function draw() {
  ctx.fillStyle = "#080c1f";
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  
  stars.forEach(s => {
    s.opacity += s.speed;
    if(s.opacity > 1 || s.opacity < 0) s.speed *= -1;
    
    ctx.beginPath();
    ctx.arc(s.x, s.y, s.size, 0, Math.PI*2);
    // Usamos concatenación tradicional para evitar errores de Jekyll
    ctx.fillStyle = "rgba(255, 255, 255, " + Math.abs(s.opacity) + ")";
    ctx.fill();
  });
  requestAnimationFrame(draw);
}

window.addEventListener('resize', init);
init();
draw();
</script>
{% endraw %}
