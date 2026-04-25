---
layout: post
title: "¿Qué es PYTHON?"
---

Aprende Python desde cero...

{% raw %}
<style>
  #python-mindmap-container { 
    min-height: 640px; 
    position: relative; 
    border-radius: 12px; 
    overflow: hidden; 
    font-family: sans-serif;
    background: #080c1f; /* Fondo de seguridad si el canvas falla */
  }
  #python-mindmap-container * { box-sizing: border-box; }
  canvas#space { position: absolute; inset: 0; width: 100%; height: 100%; z-index: 1; }
  .content { position: relative; z-index: 2; color: white; }
  .header { text-align: center; padding: 20px; }
  .header h1 { font-size: 13px; color: #4fc8d4; text-transform: uppercase; margin: 0; }
  .header p { font-size: 22px; color: #e8f4f8; margin: 5px 0; }
  .diagram-area { position: relative; width: 100%; height: 420px; }
  .center-node { position: absolute; left: 50%; top: 50%; transform: translate(-50%, -50%); width: 90px; height: 90px; border-radius: 50%; background: #0d1f45; border: 2px solid #4fc8d4; display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; z-index: 10; box-shadow: 0 0 20px rgba(79,200,212,0.4); }
  .orbit-node { position: absolute; width: 68px; height: 68px; border-radius: 50%; background: #0d2035; border: 1.5px solid #2a8aaa; display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; z-index: 5; }
  .orbit-node .icon { font-size: 18px; }
  .orbit-node .label { font-size: 8px; color: #4fc8d4; text-align: center; margin-top: 3px; max-width: 60px; }
  .modal-overlay { display: none; position: absolute; inset: 0; background: rgba(5,8,25,0.9); z-index: 100; align-items: center; justify-content: center; }
  .modal-overlay.open { display: flex; }
  .modal { background: #081228; border: 1.5px solid #4fc8d4; border-radius: 12px; padding: 25px; max-width: 400px; width: 85%; position: relative; text-align: center; }
  .modal-close { position: absolute; top: 10px; right: 10px; background: none; border: none; color: #4fc8d4; font-size: 20px; cursor: pointer; }
  .modal-tag { display: inline-block; background: rgba(79,200,212,0.1); border: 0.5px solid #4fc8d4; color: #7de8f0; border-radius: 20px; font-size: 9px; padding: 2px 8px; margin: 3px; }
</style>

<div id="python-mindmap-container">
  <canvas id="space"></canvas>
  <div class="content">
    <div class="header">
      <h1>Programación con</h1>
      <p>Python para el análisis de datos</p>
    </div>
    <div class="diagram-area">
      <div class="center-node" onclick="openCenter()">
        <span style="color:#7de8f0">PYTHON</span>
        <small style="font-size:9px">¿QUÉ ES?</small>
      </div>
      <div class="orbit-node" style="left:calc(50% - 34px);top:10px;" onclick="openNode(0)">
        <span class="icon">🔷</span><span class="label">Objetos</span>
      </div>
      <div class="orbit-node" style="left:calc(50% + 80px);top:50px;" onclick="openNode(1)">
        <span class="icon">🧠</span><span class="label">Alto nivel</span>
      </div>
      <div class="orbit-node" style="left:calc(50% - 150px);top:50px;" onclick="openNode(7)">
        <span class="icon">📊</span><span class="label">Análisis</span>
      </div>
    </div>
    <div style="text-align:center; padding-bottom:20px;">
      <button onclick="openCenter()" style="background:none; border:1px solid #4fc8d4; color:#7de8f0; border-radius:20px; padding:8px 16px; cursor:pointer;">EXPLORAR CARACTERÍSTICAS</button>
    </div>
  </div>

  <div class="modal-overlay" id="modal" onclick="if(event.target==this) closeModal()">
    <div class="modal">
      <button class="modal-close" onclick="closeModal()">✕</button>
      <div id="mIcon" style="font-size:30px"></div>
      <div id="mTitle" style="font-size:18px; color:#7de8f0; margin:10px 0;"></div>
      <div id="mBody" style="font-size:13px; color:#c0dde8; line-height:1.6;"></div>
      <div id="mTags" style="margin-top:15px;"></div>
    </div>
  </div>
</div>

<script>
const nodesData = [
  { icon:"🔷", title:"Orientado a objetos", body:"Python organiza el código en clases y objetos para modelar la realidad.", tags:["Clases","Herencia"] },
  { icon:"🧠", title:"Alto nivel", body:"Sintaxis amigable y cercana al lenguaje humano.", tags:["Legibilidad","Abstracción"] },
  { icon:"📊", title:"Análisis de datos", body:"Estándar de la industria con librerías como Pandas y NumPy.", tags:["Pandas","NumPy"] }
];

function openNode(i) {
  const n = nodesData[i] || nodesData[0];
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
  document.getElementById('mBody').textContent = 'Es un lenguaje interpretado y popular para ciencia de datos.';
  document.getElementById('mTags').innerHTML = '';
  document.getElementById('modal').classList.add('open');
}

function closeModal() {
  document.getElementById('modal').classList.remove('open');
}

// Lógica simplificada del espacio para asegurar ejecución
const canvas = document.getElementById('space');
const ctx = canvas.getContext('2d');
function resize() {
  canvas.width = canvas.parentElement.offsetWidth;
  canvas.height = canvas.parentElement.offsetHeight;
}
window.onresize = resize;
resize();

function animate() {
  ctx.fillStyle = '#080c1f';
  ctx.fillRect(0,0,canvas.width,canvas.height);
  // Aquí puedes poner tu lógica de estrellas si el build funciona
  requestAnimationFrame(animate);
}
animate();
</script>
{% endraw %}
