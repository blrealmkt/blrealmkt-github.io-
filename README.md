<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0, user-scalable=yes">
<title>¡Arma tu quiniela! — 123KLAN Style</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@400;500;600;700;800;900&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
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
  --gold: #D4A820;
  --font-display: 'Barlow Condensed', sans-serif;
  --font-mono: 'Space Mono', monospace;
}

body {
  background: var(--bg);
  font-family: var(--font-display), sans-serif;
  margin: 0;
  padding: 15px;
  color: var(--ink);
  overflow-x: hidden;
  min-height: 100vh;
  -webkit-tap-highlight-color: transparent;
}

.header-section {
  margin-bottom: 20px;
  border-bottom: 3px solid var(--fire);
  padding-bottom: 10px;
}
.header-section h1 {
  font-size: 38px;
  font-weight: 900;
  text-transform: uppercase;
  margin: 0;
  line-height: 1;
  white-space: nowrap; /* Asegura un solo renglón */
}
.header-section h1 span { color: var(--fire); }
.header-section p {
  font-family: var(--font-mono);
  font-size: 13px;
  text-transform: uppercase;
  margin: 6px 0 0;
  color: var(--ink2);
  letter-spacing: 0.08em;
}

/* ── ONBOARDING INTERACTIVO ── */
.onboarding-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(26,25,21,0.96);
  z-index: 9999;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: #fff;
  text-align: center;
  opacity: 1;
  transition: opacity 0.5s ease-out, pointer-events 0.5s;
  padding: 20px;
}
.onboarding-overlay.hidden {
  opacity: 0;
  pointer-events: none;
}
.pinch-icon {
  font-size: 80px;
  margin-bottom: 20px;
  animation: pulseFinger 1.8s infinite ease-in-out;
  display: inline-block;
}
@keyframes pulseFinger {
  0%, 100% { transform: scale(1); opacity: 1; }
  50% { transform: scale(0.8); opacity: 0.5; }
}
.onboarding-title { 
  font-size: 26px; 
  font-weight: 900; 
  text-transform: uppercase;
  margin: 0 0 10px 0;
}
.onboarding-desc {
  font-size: 14px;
  max-width: 290px;
  line-height: 1.5;
  opacity: 0.8;
}

/* ── CONTENEDOR CANVAS OPTIMIZADO PARA LIENZO MÓVIL VERTICAL ── */
.canvas-frame-container {
  width: 100%;
  height: 72vh;
  overflow: auto;
  border: 4px solid var(--ink);
  background: var(--bg2);
  box-shadow: 6px 6px 0 var(--ink);
  position: relative;
  cursor: grab;
  border-radius: 4px;
  touch-action: none;
}
.canvas-frame-container:active {
  cursor: grabbing;
}

/* REGLAS NATIVAS PARA PANTALLA COMPLETA EXCLUSIVA DE LA TABLA */
.canvas-frame-container:fullscreen {
  width: 100vw;
  height: 100vh;
  background: var(--bg2);
  padding: 15px;
  overflow: auto;
}
.canvas-frame-container:-webkit-full-screen {
  width: 100vw;
  height: 100vh;
  background: var(--bg2);
  padding: 15px;
  overflow: auto;
}

.viewport-scaler-area {
  padding: 40px;
  transform-origin: top left;
  display: grid;
  grid-template-columns: repeat(6, 265px);
  gap: 35px;
  width: max-content;
  min-height: 100%;
}

.bracket-column {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  position: relative;
}
.bracket-column-title {
  font-weight: 900;
  font-size: 16px;
  text-transform: uppercase;
  color: #fff;
  background: var(--ink);
  padding: 8px;
  border: 2px solid var(--fire);
  text-align: center;
  transform: rotate(-1.5deg);
  box-shadow: 3px 3px 0 var(--fire);
  margin-bottom: 20px;
}

/* ── NODOS ELIMINATORIOS ── */
.match-node-block {
  background: var(--white);
  border: 2.5px solid var(--ink);
  border-radius: 4px;
  padding: 8px 10px;
  box-shadow: 4px 4px 0 var(--ink);
  margin: 14px 0;
}
.node-info-row {
  display: flex;
  justify-content: space-between;
  font-family: var(--font-mono);
  font-size: 8px;
  font-weight: 700;
  color: var(--ink2);
  border-bottom: 1px dashed var(--bg3);
  padding-bottom: 4px;
  margin-bottom: 6px;
  text-transform: uppercase;
}
.node-match-id { 
  background: var(--ink); 
  color: #fff; 
  padding: 1px 5px; 
}
.team-selectable-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 15px;
  font-weight: 800;
  padding: 7px 8px;
  margin: 4px 0;
  border: 1.5px solid transparent;
  border-radius: 3px;
  cursor: pointer;
  transition: all 0.1s ease;
  text-transform: uppercase;
}
.team-selectable-row:hover {
  background: var(--fire-light);
  border-color: var(--fire);
}
.team-selectable-row.selected-winner {
  background: var(--ink);
  color: #fff;
  border-color: var(--ink);
}
.score-box-display {
  font-family: var(--font-mono);
  background: var(--bg3);
  padding: 2px 6px;
  font-size: 11px;
  border-radius: 2px;
  color: var(--ink);
  font-weight: 900;
}
.team-selectable-row.selected-winner .score-box-display {
  background: var(--fire);
  color: #fff;
}
.fav-badge {
  font-family: var(--font-mono);
  font-size: 9px;
  color: var(--fire);
  font-weight: bold;
  background: var(--fire-light);
  padding: 1px 5px;
  border-radius: 2px;
}
.team-selectable-row.selected-winner .fav-badge {
  color: var(--white);
  background: rgba(255,255,255,0.2);
}
.unresolved-node {
  opacity: 0.55;
  border-style: dashed;
  box-shadow: none;
}
.unresolved-node .team-selectable-row {
  color: var(--ink3);
  font-weight: 500;
}

/* ── PANEL DE ACCIONES ── */
.bracket-controls-panel {
  display: flex;
  gap: 8px;
  margin-bottom: 12px;
  flex-wrap: wrap;
}
.bracket-ctrl-btn {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 12px;
  letter-spacing: .04em;
  text-transform: uppercase;
  background: var(--ink);
  color: #fff;
  border: none;
  padding: 8px 14px;
  cursor: pointer;
  box-shadow: 2px 2px 0 var(--fire);
}
.bracket-ctrl-btn:active {
  transform: translate(1px, 1px);
  box-shadow: 1px 1px 0 var(--fire);
}
</style>
</head>
<body>

<div class="onboarding-overlay" id=\"onboarding-screen\" onclick=\"closeOnboarding()\">
  <div class="pinch-icon">✌️</div>
  <div class="onboarding-title">Pellizca para hacer Zoom</div>
  <div class="onboarding-desc">Usa tus dedos para ajustar la escala. Arrastra en cualquier dirección para moverte libremente por las fases de tu quiniela.</div>
</div>

<div class="header-section">
  <h1>¡Arma tu <span>quiniela!</span></h1>
  <p>El mundial es ahora</p>
</div>

<div class="bracket-controls-panel">
  <button class="bracket-ctrl-btn" onclick="toggleFullscreenCanvas()">Pantalla Completa 📸</button>
  <button class="bracket-ctrl-btn" style="background:var(--fire-dark);" onclick="resetUserQuiniela()">Reiniciar Quiniela 🔄</button>
</div>

<div class="canvas-frame-container" id="canvas-container-scroll">
  <div class="viewport-scaler-area" id="render-viewport-area">
    </div>
</div>

<script>
const SIMULATOR_DATA = [
  // ── DIECISEISAVOS DE FINAL
  { id:73, phase:'dieciseisavos', nextId:89, slot:'home', home:'Sudáfrica', homeFlag:'🇿🇦', away:'Canadá', awayFlag:'🇨🇦', homeScore:0, awayScore:1, status:'done', date:'28 Jun' },
  { id:74, phase:'dieciseisavos', nextId:89, slot:'away', home:'Alemania', homeFlag:'🇩🇪', fav:'75%', away:'Paraguay', awayFlag:'🇵🇾', homeScore:null, awayScore:null, status:'scheduled', date:'29 Jun' },
  { id:75, phase:'dieciseisavos', nextId:90, slot:'home', home:'Países Bajos', homeFlag:'🇳🇱', fav:'50%', away:'Marruecos', awayFlag:'🇲🇦', homeScore:null, awayScore:null, status:'scheduled', date:'29 Jun' },
  { id:76, phase:'dieciseisavos', nextId:90, slot:'away', home:'Brasil', homeFlag:'🇧🇷', fav:'65%', away:'Japón', awayFlag:'🇯🇵', homeScore:null, awayScore:null, status:'scheduled', date:'29 Jun' },
  { id:77, phase:'dieciseisavos', nextId:91, slot:'home', home:'Francia', homeFlag:'🇫🇷', fav:'80%', away:'Suecia', awayFlag:'🇸🇪', homeScore:null, awayScore:null, status:'scheduled', date:'30 Jun' },
  { id:78, phase:'dieciseisavos', nextId:91, slot:'away', home:'Costa de Marfil', homeFlag:'🇨🇮', away:'Noruega', awayFlag:'🇳🇴', favAway:'56%', homeScore:null, awayScore:null, status:'scheduled', date:'30 Jun' },
  { id:79, phase:'dieciseisavos', nextId:92, slot:'home', home:'México', homeFlag:'🇲🇽', fav:'51%', away:'Ecuador', awayFlag:'🇪🇨', homeScore:null, awayScore:null, status:'scheduled', date:'30 Jun' },
  { id:80, phase:'dieciseisavos', nextId:92, slot:'away', home:'Inglaterra', homeFlag:'🏴\u200d󠁢󠁥󠁮󠁧󠁿', fav:'80%', away:'RD Congo', awayFlag:'🇨🇩', homeScore:null, awayScore:null, status:'scheduled', date:'01 Jul' },
  { id:81, phase:'dieciseisavos', nextId:93, slot:'home', home:'Estados Unidos', homeFlag:'🇺🇸', fav:'70%', away:'Bosnia', awayFlag:'🇧🇦', homeScore:null, awayScore:null, status:'scheduled', date:'01 Jul' },
  { id:82, phase:'dieciseisavos', nextId:93, slot:'away', home:'Bélgica', homeFlag:'🇧🇪', fav:'45%', away:'Senegal', awayFlag:'🇸🇳', homeScore:null, awayScore:null, status:'scheduled', date:'01 Jul' },
  { id:83, phase:'dieciseisavos', nextId:94, slot:'home', home:'Portugal', homeFlag:'🇵🇹', fav:'60%', away:'Croacia', awayFlag:'🇭🇷', homeScore:null, awayScore:null, status:'scheduled', date:'02 Jul' },
  { id:84, phase:'dieciseisavos', nextId:94, slot:'away', home:'España', homeFlag:'🇪🇸', fav:'80%', away:'Austria', awayFlag:'🇦🇹', homeScore:null, awayScore:null, status:'scheduled', date:'02 Jul' },
  { id:85, phase:'dieciseisavos', nextId:95, slot:'home', home:'Suiza', homeFlag:'🇨🇭', fav:'55%', away:'Argelia', awayFlag:'🇩🇿', homeScore:null, awayScore:null, status:'scheduled', date:'02 Jul' },
  { id:86, phase:'dieciseisavos', nextId:95, slot:'away', home:'Argentina', homeFlag:'🇦🇷', fav:'90%', away:'Cabo Verde', awayFlag:'🇨🇻', homeScore:null, awayScore:null, status:'scheduled', date:'03 Jul' },
  { id:87, phase:'dieciseisavos', nextId:96, slot:'home', home:'Colombia', homeFlag:'🇨🇴', fav:'70%', away:'Ghana', awayFlag:'🇬🇭', homeScore:null, awayScore:null, status:'scheduled', date:'03 Jul' },
  { id:88, phase:'dieciseisavos', nextId:96, slot:'away', home:'Australia', homeFlag:'🇦🇺', away:'Egipto', awayFlag:'🇪🇬', favAway:'45%', homeScore:null, awayScore:null, status:'scheduled', date:'03 Jul' },
  
  // ── OCTAVOS DE FINAL
  { id:89, phase:'octavos', nextId:97, slot:'home', home:'Canadá', homeFlag:'🇨🇦', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, status:'scheduled', date:'04 Jul' },
  { id:90, phase:'octavos', nextId:97, slot:'away', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, status:'scheduled', date:'04 Jul' },
  { id:91, phase:'octavos', nextId:98, slot:'home', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, status:'scheduled', date:'05 Jul' },
  { id:92, phase:'octavos', nextId:98, slot:'away', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, status:'scheduled', date:'05 Jul' },
  { id:93, phase:'octavos', nextId:99, slot:'home', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, status:'scheduled', date:'06 Jul' },
  { id:94, phase:'octavos', nextId:99, slot:'away', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, status:'scheduled', date:'06 Jul' },
  { id:95, phase:'octavos', nextId:100, slot:'home', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, status:'scheduled', date:'07 Jul' },
  { id:96, phase:'octavos', nextId:100, slot:'away', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, status:'scheduled', date:'07 Jul' },
  
  // ── CUARTOS DE FINAL
  { id:97, phase:'cuartos', nextId:101, slot:'home', home:'Ganador M89', homeFlag:'⚽', away:'Ganador M90', awayFlag:'⚽', homeScore:null, awayScore:null, status:'scheduled', date:'09 Jul' },
  { id:98, phase:'cuartos', nextId:101, slot:'away', home:'Ganador M91', homeFlag:'⚽', away:'Ganador M92', awayFlag:'⚽', homeScore:null, awayScore:null, status:'scheduled', date:'10 Jul' },
  { id:99, phase:'cuartos', nextId:102, slot:'home', home:'Ganador M93', homeFlag:'⚽', away:'Ganador M94', awayFlag:'⚽', homeScore:null, awayScore:null, status:'scheduled', date:'11 Jul' },
  { id:100, phase:'cuartos', nextId:102, slot:'away', home:'Ganador M95', homeFlag:'⚽', away:'Ganador M96', awayFlag:'⚽', homeScore:null, awayScore:null, status:'scheduled', date:'11 Jul' },
  
  // ── SEMIFINALES
  { id:101, phase:'semis', nextId:104, slot:'home', home:'Ganador Semis 1', homeFlag:'⚽', away:'Ganador Semis 2', awayFlag:'⚽', homeScore:null, awayScore:null, status:'scheduled', date:'14 Jul' },
  { id:102, phase:'semis', nextId:104, slot:'away', home:'Ganador Semis 3', homeFlag:'⚽', away:'Ganador Semis 4', awayFlag:'⚽', homeScore:null, awayScore:null, status:'scheduled', date:'15 Jul' },
  
  // ── TERCER LUGAR Y GRAN FINAL
  { id:103, phase:'tercer-lugar', nextId:null, slot:null, home:'Perdedor Semi 1', homeFlag:'🥉', away:'Perdedor Semi 2', awayFlag:'🥉', homeScore:null, awayScore:null, status:'scheduled', date:'18 Jul' },
  { id:104, phase:'final', nextId:null, slot:null, home:'Finalista 1', homeFlag:'🌍', away:'Finalista 2', awayFlag:'🌍', homeScore:null, awayScore:null, status:'scheduled', date:'19 Jul' }
];

let currentScale = 0.65;

function closeOnboarding() {
  document.getElementById('onboarding-screen').classList.add('hidden');
}
setTimeout(closeOnboarding, 2800);

function render() {
  const container = document.getElementById('render-viewport-area');
  const phases = ['dieciseisavos', 'octavos', 'cuartos', 'semis', 'tercer-lugar', 'final'];
  let html = '';

  phases.forEach(p => {
    let list = SIMULATOR_DATA.filter(m => m.phase === p);
    let title = p === 'tercer-lugar' ? 'Tercer Lugar' : p === 'semis' ? 'Semifinal' : p;
    html += `<div class="bracket-column"><div class="bracket-column-title">${title}</div>`;
    
    list.forEach(m => {
      const isDone = m.status === 'done';
      const isHomeWin = isDone && m.homeScore > m.awayScore;
      const isAwayWin = isDone && m.awayScore > m.homeScore;
      const isPlaceholder = m.home.includes('Por definir') || m.home.includes('Ganador') || m.home.includes('Finalista') || m.home.includes('Perdedor');

      const favHomeHTML = (m.fav && !isDone) ? `<span class="fav-badge">${m.fav}</span>` : '';
      const favAwayHTML = (m.favAway && !isDone) ? `<span class="fav-badge">${m.favAway}</span>` : '';

      html += `
        <div class="bracket-match-node ${isPlaceholder ? 'unresolved-node' : ''}">
          <div class="node-info-row"><span class="node-match-id">M${m.id}</span><span>${m.date}</span></div>
          <div class="team-selectable-row ${isHomeWin ? 'selected-winner' : ''}" onclick="advanceTeam(${m.id}, 'home')">
            <span>${m.homeFlag || '⭐'} ${m.home} ${favHomeHTML}</span>
            <span class="score-box-display">${m.homeScore !== null ? m.homeScore : '—'}</span>
          </div>
          <div class="team-selectable-row ${isAwayWin ? 'selected-winner' : ''}" onclick="advanceTeam(${m.id}, 'away')">
            <span>${m.awayFlag || '⭐'} ${m.away} ${favAwayHTML}</span>
            <span class="score-box-display">${m.awayScore !== null ? m.awayScore : '—'}</span>
          </div>
        </div>`;
    });
    html += `</div>`;
  });
  container.innerHTML = html;
  container.style.transform = `scale(${currentScale})`;
}

function advanceTeam(matchId, side) {
  if(matchId === 73) return; // Bloquear M73 real de Canadá
  const m = SIMULATOR_DATA.find(x => x.id === matchId);
  if(!m || m.home.includes('Por definir') || m.home.includes('Ganador') || m.home.includes('Finalista')) return;

  m.status = 'done';
  m.homeScore = side === 'home' ? 1 : 0;
  m.awayScore = side === 'home' ? 0 : 1;

  const winnerName = side === 'home' ? m.home : m.away;
  const winnerFlag = side === 'home' ? m.homeFlag : m.awayFlag;
  const loserName = side === 'home' ? m.away : m.home;
  const loserFlag = side === 'home' ? m.awayFlag : m.homeFlag;

  if (m.phase === 'semis') {
    const finalMatch = SIMULATOR_DATA.find(x => x.phase === 'final');
    const thirdMatch = SIMULATOR_DATA.find(x => x.phase === 'tercer-lugar');
    if(m.id === 101) {
      finalMatch.home = winnerName; finalMatch.homeFlag = winnerFlag;
      thirdMatch.home = loserName; thirdMatch.homeFlag = loserFlag;
    } else {
      finalMatch.away = winnerName; finalMatch.flagAway = winnerFlag;
      thirdMatch.away = loserName; thirdMatch.flagAway = loserFlag;
    }
  } else if(m.nextId) {
    const next = SIMULATOR_DATA.find(x => x.id === m.nextId);
    if(next) {
      if(m.slot === 'home') { next.home = winnerName; next.homeFlag = winnerFlag; }
      else { next.away = winnerName; next.awayFlag = winnerFlag; }
    }
  }
  render();
}

function resetUserQuiniela() {
  SIMULATOR_DATA.forEach(m => {
    if(m.id !== 73) { // Limpiar todo excepto Canadá
      m.homeScore = null;
      m.awayScore = null;
      m.status = 'scheduled';
      if(m.id >= 89) {
        m.home = m.id === 89 ? 'Canadá' : m.phase === 'octavos' ? 'Por definir' : 'Ganador M';
        m.homeFlag = m.id === 89 ? '🇨🇦' : '⭐';
        m.away = m.phase === 'octavos' ? 'Por definir' : 'Ganador M';
        m.awayFlag = '⭐';
      }
    }
  });
  render();
}

function toggleFullscreenCanvas() {
  const el = document.getElementById('canvas-container-scroll');
  if (!document.fullscreenElement) {
    el.requestFullscreen().catch(err => {
      alert(`Error al activar pantalla completa: ${err.message}`);
    });
  } else {
    document.exitFullscreen();
  }
}

// ── SISTEMA DE DESPLAZAMIENTO TÁCTIL ──
const frame = document.getElementById('canvas-container-scroll');
let isDragging = false; let sx, sy, sLeft, sTop;

const startPan = (e) => {
  isDragging = true;
  const x = e.pageX || e.touches[0].pageX;
  const y = e.pageY || e.touches[0].pageY;
  sx = x - frame.offsetLeft;
  sy = y - frame.offsetTop;
  sLeft = frame.scrollLeft; sTop = frame.scrollTop;
};
frame.addEventListener('mousedown', startPan);
frame.addEventListener('touchstart', startPan);

const movePan = (e) => {
  if(!isDragging) return;
  const x = e.pageX || e.touches[0].pageX;
  const y = e.pageY || e.touches[0].pageY;
  frame.scrollLeft = sLeft - (x - frame.offsetLeft - sx) * 1.4;
  frame.scrollTop = sTop - (y - frame.offsetTop - sy) * 1.4;
};
frame.addEventListener('mousemove', movePan);
frame.addEventListener('touchmove', movePan);

window.addEventListener('mouseup', () => isDragging = false);
frame.addEventListener('touchend', () => isDragging = false);

render();
</script>
</body>
</html>
