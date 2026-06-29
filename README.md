<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0, user-scalable=yes">
<title>Prototipo Quiniela 123KLAN</title>
<style>
:root {
  --bg: #F5F2EB;
  --bg2: #EDE9DF;
  --bg3: #E3DFD4;
  --white: #FFFFFF;
  --ink: #1A1915;
  --ink2: #3D3C36;
  --fire: #FF4D1C;
  --fire-light: #FFE8E1;
  --fire-dark: #CC3A12;
  --font-display: 'Barlow Condensed', sans-serif;
  --font-mono: 'Space Mono', monospace;
}

body {
  background: var(--bg);
  font-family: sans-serif;
  margin: 0;
  padding: 10px;
  color: var(--ink);
  overflow-x: hidden;
}

/* PANEL DE CONTROLES GRAFFITI */
.controls-panel {
  display: flex;
  gap: 8px;
  margin-bottom: 12px;
  background: var(--bg3);
  padding: 10px;
  border: 2px solid var(--ink);
  box-shadow: 3px 3px 0 var(--ink);
}
.ctrl-btn {
  font-family: 'Arial Black', sans-serif;
  text-transform: uppercase;
  font-size: 11px;
  background: var(--ink);
  color: #fff;
  border: none;
  padding: 8px 12px;
  cursor: pointer;
  box-shadow: 2px 2px 0 var(--fire);
}
.ctrl-btn:active {
  transform: translate(1px, 1px);
  box-shadow: 1px 1px 0 var(--fire);
}

/* CONTENEDOR MÓVIL: LIENZO INFINITO DE ARRASTRE */
.canvas-container {
  width: 100%;
  height: 70vh;
  overflow: auto;
  border: 3px solid var(--ink);
  background: var(--bg2);
  box-shadow: 4px 4px 0 var(--ink);
  cursor: grab;
  position: relative;
  touch-action: none; /* Desactiva scroll nativo para manejarlo por JS */
}
.canvas-container:active {
  cursor: grabbing;
}

/* ÁREA INTERNA TRANSFORMABLE POR ZOOM */
.viewport-transform {
  padding: 40px;
  transform-origin: top left;
  display: grid;
  grid-template-columns: repeat(5, 260px);
  gap: 30px;
  width: max-content;
}

.bracket-column {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
.column-title {
  font-family: 'Arial Black', sans-serif;
  font-size: 14px;
  text-transform: uppercase;
  color: #fff;
  background: var(--ink);
  padding: 6px;
  border: 2px solid var(--fire);
  text-align: center;
  transform: rotate(-1.5deg);
  box-shadow: 3px 3px 0 var(--fire);
  margin-bottom: 15px;
}

/* NODOS INTERACTIVOS DE QUINIELA */
.match-node {
  background: var(--white);
  border: 2px solid var(--ink);
  border-radius: 4px;
  padding: 8px;
  box-shadow: 3px 3px 0 var(--ink);
  margin: 10px 0;
}
.node-header {
  display: flex;
  justify-content: space-between;
  font-size: 9px;
  color: #666;
  border-bottom: 1px dashed var(--bg3);
  padding-bottom: 4px;
  margin-bottom: 6px;
}
.node-id {
  background: var(--ink);
  color: #fff;
  padding: 1px 4px;
  font-weight: bold;
}
.team-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 14px;
  font-weight: bold;
  padding: 6px;
  margin: 2px 0;
  border: 1.5px solid transparent;
  cursor: pointer;
  border-radius: 3px;
  transition: all 0.1s ease;
}
.team-row:hover {
  background: var(--fire-light);
  border-color: var(--fire);
}
.team-row.winner-active {
  background: var(--ink);
  color: #fff;
  border-color: var(--ink);
}
.score-box {
  background: var(--bg3);
  padding: 1px 6px;
  font-size: 11px;
  border-radius: 2px;
}
.team-row.winner-active .score-box {
  background: var(--fire);
  color: #fff;
}
.unresolved {
  opacity: 0.5;
  border-style: dashed;
}
</style>
</head>
<body>

  <div class="controls-panel">
    <button class="ctrl-btn" onclick="zoomCanvas(0.15)">Zoom +</button>
    <button class="ctrl-btn" onclick="zoomCanvas(-0.15)">Zoom -</button>
    <button class="ctrl-btn" onclick="resetCanvas()">Centrar</button>
  </div>

  <div class="canvas-container" id="canvas-container">
    <div class="viewport-transform" id="viewport-transform">
      </div>
  </div>

<script>
// Base de datos reducida para simulación lineal
const QUINIELA_DATA = [
  { id:73, phase:'dieciseisavos', nextId:89, slot:'home', home:'Sudáfrica', homeFlag:'🇿🇦', away:'Canadá', awayFlag:'🇨🇦', homeScore:null, awayScore:null },
  { id:74, phase:'dieciseisavos', nextId:89, slot:'away', home:'Alemania', homeFlag:'🇩🇪', away:'Paraguay', awayFlag:'🇵🇾', homeScore:null, awayScore:null },
  { id:89, phase:'octavos', nextId:97, slot:'home', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null },
  { id:97, phase:'cuartos', nextId:101, slot:'home', home:'Ganador M89', homeFlag:'⚽', away:'Ganador M90', awayFlag:'⚽', homeScore:null, awayScore:null },
  { id:101, phase:'semis', nextId:104, slot:'home', home:'Ganador M97', homeFlag:'⚽', away:'Ganador M98', awayFlag:'⚽', homeScore:null, awayScore:null },
  { id:104, phase:'final', nextId:null, slot:null, home:'Finalista 1', homeFlag:'🌎', away:'Finalista 2', awayFlag:'🌎', homeScore:null, awayScore:null }
];

let currentZoom = 0.9;

function renderPrototype() {
  const container = document.getElementById('viewport-transform');
  const phases = ['dieciseisavos', 'octavos', 'cuartos', 'semis', 'final'];
  let html = '';

  phases.forEach(p => {
    let matches = QUINIELA_DATA.filter(m => m.phase === p);
    if(matches.length === 0) return;
    html += `<div class="bracket-column"><div class="column-title">${p}</div>`;
    matches.forEach(m => {
      const isHomeWin = m.homeScore > m.awayScore;
      const isAwayWin = m.awayScore > m.homeScore;
      html += `
        <div class="match-node">
          <div class="node-header"><span class="node-id">M${m.id}</span></div>
          <div class="team-row ${isHomeWin ? 'winner-active' : ''}" onclick="selectWinner(${m.id}, 'home')">
            <span>${m.homeFlag} ${m.home}</span><span class="score-box">${m.homeScore !== null ? m.homeScore : '—'}</span>
          </div>
          <div class="team-row ${isAwayWin ? 'winner-active' : ''}" onclick="selectWinner(${m.id}, 'away')">
            <span>${m.awayFlag} ${m.away}</span><span class="score-box">${m.awayScore !== null ? m.awayScore : '—'}</span>
          </div>
        </div>`;
    });
    html += `</div>`;
  });
  container.innerHTML = html;
  container.style.transform = `scale(${currentZoom})`;
}

function selectWinner(matchId, side) {
  const match = QUINIELA_DATA.find(m => m.id === matchId);
  if(!match || match.home.includes('Ganador') || match.home.includes('Por definir')) return;

  if(side === 'home') { match.homeScore = 1; match.awayScore = 0; } 
  else { match.homeScore = 0; match.awayScore = 1; }

  const winner = side === 'home' ? match.home : match.away;
  const flag = side === 'home' ? match.homeFlag : match.awayFlag;

  if(match.nextId) {
    const nextMatch = QUINIELA_DATA.find(m => m.id === match.nextId);
    if(nextMatch) {
      if(match.slot === 'home') { nextMatch.home = winner; nextMatch.homeFlag = flag; } 
      else { nextMatch.away = winner; nextMatch.awayFlag = flag; }
    }
  }
  renderPrototype();
}

function zoomCanvas(v) { currentZoom = Math.min(Math.max(0.4, currentZoom + v), 1.8); renderPrototype(); }
function resetCanvas() { currentZoom = 0.9; renderPrototype(); }

// MOTOR DE ARRASTRE (DRAG TO SCROLL) PARA TOUCH Y MOUSE
const slider = document.getElementById('canvas-container');
let isDown = false; let startX, startY, scrollLeft, scrollTop;

const startDrag = (e) => {
  isDown = true;
  const pageX = e.pageX || e.touches[0].pageX;
  const pageY = e.pageY || e.touches[0].pageY;
  startX = pageX - slider.offsetLeft;
  startY = pageY - slider.offsetTop;
  scrollLeft = slider.scrollLeft;
  scrollTop = slider.scrollTop;
};
const stopDrag = () => isDown = false;
const moveDrag = (e) => {
  if(!isDown) return;
  e.preventDefault();
  const pageX = e.pageX || e.touches[0].pageX;
  const pageY = e.pageY || e.touches[0].pageY;
  const x = pageX - slider.offsetLeft;
  const y = pageY - slider.offsetTop;
  slider.scrollLeft = scrollLeft - (x - startX) * 1.5;
  slider.scrollTop = scrollTop - (y - startY) * 1.5;
};

slider.addEventListener('mousedown', startDrag);
slider.addEventListener('mouseleave', stopDrag);
slider.addEventListener('mouseup', stopDrag);
slider.addEventListener('mousemove', moveDrag);
slider.addEventListener('touchstart', startDrag);
slider.addEventListener('touchend', stopDrag);
slider.addEventListener('touchmove', moveDrag);

renderPrototype();
</script>
</body>
</html>
