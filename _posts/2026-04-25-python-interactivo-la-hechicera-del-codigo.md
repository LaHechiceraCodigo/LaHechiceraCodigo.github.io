---
layout: post
title: "¿Qué es PYTHON?"
---

Aprende Python desde cero...

{% raw %}
<style>
  /* Contenedor principal con ID único para no romper el blog */
  #python-mindmap-container { 
    min-height: 640px; 
    position: relative; 
    border-radius: 12px; 
    overflow: hidden; 
    font-family: sans-serif;
    margin-top: -30px; /* Elimina el espacio extra arriba */
  }

  /* Evita que los estilos afecten al resto del blog */
  #python-mindmap-container * { box-sizing: border-box; margin: 0; padding: 0; }
  
  canvas#space { position: absolute; inset: 0; width: 100%; height: 100%; border-radius: 12px; }
  .content { position: relative; z-index: 2; }
  .header { text-align: center; padding: 15px 20px 5px; }
  .header h1 { font-size: 13px; font-weight: 500; letter-spacing: 0.2em; color: #4fc8d4; text-transform: uppercase; margin: 0; }
  .header p { font-size: 22px; font-weight: 500; color: #e8f4f8; margin-top: 4px; }
  
  /* ... (He mantenido el resto de tus estilos del archivo original) ... */
  .diagram-area { position: relative; width: 100%; height: 420px; }
  svg.connections { position: absolute; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; }
  .center-node { position: absolute; left: 50%; top: 50%; transform: translate(-50%, -50%); width: 90px; height: 90px; border-radius: 50%; background: radial-gradient(circle, #1a3a6e 0%, #0d1f45 100%); border: 2px solid #4fc8d4; display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; z-index: 10; box-shadow: 0 0 24px rgba(79,200,212,0.35); }
  .orbit-node { position: absolute; width: 68px; height: 68px; border-radius: 50%; background: radial-gradient(circle, #1a4060 0%, #0d2035 100%); border: 1.5px solid #2a8aaa; display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; z-index: 5; }
  .orbit-node .icon { font-size: 18px; }
  .orbit-node .label { font-size: 8px; color: #4fc8d4; text-align: center; margin-top: 3px; line-height: 1.2; max-width: 60px; }
  .modal-overlay { display: none; position: absolute; inset: 0; background: rgba(5,8,25,0.88); z-index: 50; align-items: center; justify-content: center; border-radius: 12px; }
  .modal-overlay.open { display: flex; }
  .modal { background: linear-gradient(145deg, #0e1a3d, #081228); border: 1.5px solid #4fc8d4; border-radius: 12px; padding: 28px; max-width: 460px; width: 90%; position: relative; }
  .modal-close { position: absolute; top: 12px; right: 16px; background: none; border: none; color: #4fc8d4; font-size: 20px; cursor: pointer; }
  .permite-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-top: 14px; }
  .permite-card { background: rgba(79,200,212,0.06); border: 0.5px solid #2a5a7a; border-radius: 8px; padding: 12px 10px; text-align: center; cursor: pointer; }
  .p-icon { font-size: 22px; }
  .p-title { font-size: 10px; color: #7de8f0; font-weight: 500; }
  .footer-hint { text-align: center; padding: 0 20px 20px; }
  .footer-hint p { font-size: 11px; color: #4fc8d4; }
  .footer-hint button { background: rgba(79,200,212,0.1); border: 1px solid #4fc8d4; color: #7de8f0; border-radius: 20px; padding: 7px 20px; font-size: 11px; cursor: pointer; }
</style>

<div id="python-mindmap-container">
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
        <span class="icon">🌐</span><span class="label">Escalable</span>
      </div>
      <div class="orbit-node" id="n4" style="left:calc(50% - 34px);top:338px;" onclick="openNode(4)">
        <span class="icon">🤝</span><span class="label">Colaborativo</span>
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
      <hr style="border:none; border-top:0.5px solid #2a5a7a; margin:12px 0;">
      <div id="mBody" style="font-size:13px; color:#c0dde8; line-height:1.7;"></div>
    </div>
  </div>
</div>

<script>
// Usamos concatenación tradicional en lugar de `${}` para que Jekyll no se rompa si algo falla
function openPermite() {
  document.getElementById('mIcon').textContent = '⚡';
  document.getElementById('mTitle').textContent = 'Python permite...';
  document.getElementById('mSubtitle').textContent = 'Aplicaciones y casos de uso';
  
  var html = '<div class="permite-grid">';
  // Usamos un bucle simple y evitamos el símbolo $ para mayor seguridad
  var items = [
    { i:"🌍", t:"Aplicaciones Web" },
    { i:"📊", t:"Análisis de datos" },
    { i:"🔍", t:"Web Scraping" },
    { i:"🎮", t:"Videojuegos" },
    { i:"🖥️", t:"Apps de escritorio" }
  ];
  
  for(var i=0; i<items.length; i++) {
    html += '<div class="permite-card" onclick="openPermiteDetail(' + i + ')">';
    html += '<div class="p-icon">' + items[i].i + '</div>';
    html += '<div class="p-title">' + items[i].t + '</div>';
    html += '</div>';
  }
  html += '</div>';
  
  document.getElementById('mBody').innerHTML = html;
  document.getElementById('modal').classList.add('open');
}

// ... El resto de tus funciones closeModal, openNode, etc. deben ir aquí ...
// Asegúrate de que el código del canvas (drawFrame) esté al final del script.
</script>
{% endraw %}
