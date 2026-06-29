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
  font-size: 42px;
  font-weight: 900;
  text-transform: uppercase;
  margin: 0;
  line-height: 1;
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

/* ── ONBOARDING INTERACTIVO CON DESVANECIMIENTO ── */
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
  transition: opacity 0.6s cubic-bezier(0.25, 1, 0.5, 1), pointer-events 0.6s;
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
  0%, 100% { transform: scale(1) rotate(0deg); opacity: 1; }
  50% { transform: scale(0.8) rotate(-5deg); opacity: 0.5; }
}
.onboarding-title { 
  font-size: 26px; 
  font-weight: 900; 
  text-transform: uppercase;
  margin: 0 0 10px 0;
  letter-spacing: 0.05em;
}
.onboarding-desc {
  font-size: 14px;
  max-width: 290px;
  line-height: 1.5;
  opacity: 0.8;
  margin: 0;
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
  touch-action: none; /* Bloquea el scroll nativo para el paneo controlado */
}
.canvas-frame-container:active {
  cursor: grabbing;
}

.viewport-scaler-area {
  padding: 40px;
  transform-origin: top left;
  display: grid;
  grid-template-columns: repeat(6, 265px); /* 6 Columnas: Dieciseisavos a Final */
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
  letter-spacing: 0.05em;
}

/* ── TARJETAS ELIMINATORIAS DE QUINIELA ── */
.match-node-block {
  background: var(--white);
  border: 2.5px solid var(--ink);
  border-radius: 4px;
  padding: 8px 10px;
  box-shadow: 4px 4px 0 var(--ink);
  margin: 14px 0;
  position: relative;
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
  padding: 1px 6px;
  font-size: 11px;
  border-radius: 2px;
  color: var(--ink);
  font-weight: 700;
}
.team-selectable-row.selected-winner .score-box-display {
  background: var(--fire);
  color: #fff;
}
.unresolved-node {
  opacity: 0.55;
  border-style: dashed;
  box-shadow: none;
}
.unresolved-node .team-selectable-row {
  font-style: italic;
  font-weight: 500;
}

.action-bar {
  margin-bottom: 15px;
}
.center-btn {
  font-weight: 900;
  font-size: 13px;
  text-transform: uppercase;
  background: var(--ink);
  color: #fff;
  border: none;
  padding: 10px 18px;
  cursor: pointer;
  box-shadow: 3px 3px 0 var(--fire);
  transition: transform 0.05s;
}
.center-btn:active {
  transform: translate(2px, 2px);
  box-shadow: 1px 1px 0 var(--fire);
}
</style>
</head>
<body>

<div class="onboarding-overlay" id="onboarding-screen" onclick="closeOnboarding()">
  <div class="pinch-icon\">✌️</div>
  <div class="onboarding-title">Pellizca para hacer Zoom</div>
  <div class="onboarding-desc">Usa dos dedos en tu pantalla móvil para ajustar el tamaño del cuadro y arrastra en cualquier dirección para navegar libremente.</div>
</div>

<div class="header-section">
  <h1>¡Arma tu <span>quiniela!</span></h1>
  <p>El mundial es ahora</p>
</div>

<div class="action-bar">
  <button class="center-btn" onclick="resetCanvasView()">Centrar Mapa</button>
</div>

<div class="canvas-frame-container" id="canvas-container-scroll">
  <div class="viewport-scaler-area" id="render-viewport-area">
    </div>
</div>

<script>
// Base de datos completa con las 6 fases de la eliminación directa
const SIMULATOR_DATA = [
  // ── DIECISEISAVOS DE FINAL (16 Partidos)
  { id:73, phase:'dieciseisavos', nextId:89, slot:'home', home:'Sudáfrica', flag:'🇿🇦', away:'Canadá', flagAway:'🇨🇦', homeScore:null, awayScore:null, date:'28 Jun' },
  { id:74, phase:'dieciseisavos', nextId:89, slot:'away', home:'Alemania', flag:'🇩🇪', away:'Paraguay', flagAway:'🇵🇾', homeScore:null, awayScore:null, date:'29 Jun' },
  { id:75, phase:'dieciseisavos', nextId:90, slot:'home', home:'Países Bajos', flag:'🇳🇱', away:'Marruecos', flagAway:'🇲🇦', homeScore:null, awayScore:null, date:'29 Jun' },
  { id:76, phase:'dieciseisavos', nextId:90, slot:'away', home:'Brasil', flag:'🇧🇷', away:'Japón', flagAway:'🇯🇵', homeScore:null, awayScore:null, date:'29 Jun' },
  { id:77, phase:'dieciseisavos', nextId:91, slot:'home', home:'Francia', flag:'🇫🇷', away:'Suecia', flagAway:'🇸🇪', homeScore:null, awayScore:null, date:'30 Jun' },
  { id:78, phase:'dieciseisavos', nextId:91, slot:'away', home:'Costa de Marfil', flag:'🇨🇮', away:'Noruega', flagAway:'🇳🇴', homeScore:null, awayScore:null, date:'30 Jun' },
  { id:79, phase:'dieciseisavos', nextId:92, slot:'home', home:'México', flag:'🇲🇽', away:'Ecuador', flagAway:'🇪🇨', homeScore:null, awayScore:null, date:'30 Jun' },
  { id:80, phase:'dieciseisavos', nextId:92, slot:'away', home:'Inglaterra', flag:'🏴\u200d󠁢󠁥󠁮󠁧󠁿', away:'RD Congo', flagAway:'🇨🇩', homeScore:null, awayScore:null, date:'01 Jul' },
  { id:81, phase:'dieciseisavos', nextId:93, slot:'home', home:'Estados Unidos', flag:'🇺🇸', away:'Bosnia', flagAway:'🇧🇦', homeScore:null, awayScore:null, date:'01 Jul' },
  { id:82, phase:'dieciseisavos', nextId:93, slot:'away', home:'Bélgica', flag:'🇧🇪', away:'Senegal', flagAway:'🇸🇳', homeScore:null, awayScore:null, date:'01 Jul' },
  { id:83, phase:'dieciseisavos', nextId:94, slot:'home', home:'Portugal', flag:'🇵🇹', away:'Croacia', flagAway:'🇭🇷', homeScore:null, awayScore:null, date:'02 Jul' },
  { id:84, phase:'dieciseisavos', nextId:94, slot:'away', home:'España', flag:'🇪🇸', away:'Austria', flagAway:'🇦🇹', homeScore:null, awayScore:null, date:'02 Jul' },
  { id:85, phase:'dieciseisavos', nextId:95, slot:'home', home:'Suiza', flag:'🇨🇭', away:'Argelia', flagAway:'🇩🇿', homeScore:null, awayScore:null, date:'02 Jul' },
  { id:86, phase:'dieciseisavos', nextId:95, slot:'away', home:'Argentina', flag:'🇦🇷', away:'Cabo Verde', flagAway:'🇨🇻', homeScore:null, awayScore:null, date:'03 Jul' },
  { id:87, phase:'dieciseisavos', nextId:96, slot:'home', home:'Colombia', flag:'🇨🇴', away:'Ghana', flagAway:'🇬🇭', homeScore:null, awayScore:null, date:'03 Jul' },
  { id:88, phase:'dieciseisavos', nextId:96, slot:'away', home:'Australia', flag:'🇦🇺', away:'Egipto', flagAway:'🇪🇬', homeScore:null, awayScore:null, date:'03 Jul' },
  
  // ── OCTAVOS DE FINAL (8 Partidos)
  { id:89, phase:'octavos', nextId:97, slot:'home', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, date:'04 Jul' },
  { id:90, phase:'octavos', nextId:97, slot:'away', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, date:'04 Jul' },
  { id:91, phase:'octavos', nextId:98, slot:'home', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, date:'05 Jul' },
  { id:92, phase:'octavos', nextId:98, slot:'away', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, date:'05 Jul' },
  { id:93, phase:'octavos', nextId:99, slot:'home', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, date:'06 Jul' },
  { id:94, phase:'octavos', nextId:99, slot:'away', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, date:'06 Jul' },
  { id:95, phase:'octavos', nextId:100, slot:'home', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, date:'07 Jul' },
  { id:96, phase:'octavos', nextId:100, slot:'away', home:'Por definir', homeFlag:'⭐', away:'Por definir', awayFlag:'⭐', homeScore:null, awayScore:null, date:'07 Jul' },
  
  // ── CUARTOS DE FINAL (4 Partidos)
  { id:97, phase:'cuartos', nextId:101, slot:'home', home:'Ganador M89', homeFlag:'⚽', away:'Ganador M90', awayFlag:'⚽', homeScore:null, awayScore:null, date:'09 Jul' },
  { id:98, phase:'cuartos', nextId:101, slot:'away', home:'Ganador M91', homeFlag:'⚽', away:'Ganador M92', awayFlag:'⚽', homeScore:null, awayScore:null, date:'10 Jul' },
  { id:99, phase:'cuartos', nextId:102, slot:'home', home:'Ganador M93', homeFlag:'⚽', away:'Ganador M94', awayFlag:'⚽', homeScore:null, awayScore:null, date:'11 Jul' },
  { id:100, phase:'cuartos', nextId:102, slot:'away', home:'Ganador M95', homeFlag:'⚽', away:'Ganador M96', awayFlag:'⚽', homeScore:null, awayScore:null, date:'11 Jul' },
  
  // ── SEMIFINALES (2 Partidos)
  { id:101, phase:'semis', nextId:104, slot:'home', home:'Ganador Cuartos 1', homeFlag:'⚽', away:'Ganador Cuartos 2', awayFlag:'⚽', homeScore:null, awayScore:null, date:'14 Jul' },
  { id:102, phase:'semis', nextId:104, slot:'away', home:'Ganador Cuartos 3', homeFlag:'⚽', away:'Ganador Cuartos 4', awayFlag:'⚽', homeScore:null, awayScore:null, date:'15 Jul' },
  
  // ── TERCER LUGAR (1 Partido)
  { id:103, phase:'tercer-lugar', nextId:null, slot:null, home:'Perdedor Semi 1', homeFlag:'🥉', away:'Perdedor Semi 2', awayFlag:'🥉', homeScore:null, awayScore:null, date:'18 Jul' },
  
  // ── GRAN FINAL (1 Partido)
  { id:104, phase:'final', nextId:null, slot:null, home:'Finalista 1', homeFlag:'🌍', away:'Finalista 2', awayFlag:'🌍', homeScore:null, awayScore:null, date:'19 Jul' }
];

let globalZoom = 0.65; // Zoom idóneo preestablecido para visualización vertical

function closeOnboarding() {
  document.getElementById('onboarding-screen').classList.add('hidden');
}
setTimeout(closeOnboarding, 3200); // Se desvanece de forma automatizada a los 3 segundos

function render() {
  const container = document.getElementById('render-viewport-area');
  const rounds = ['dieciseisavos', 'octavos', 'cuartos', 'semis', 'tercer-lugar', 'final'];
  let html = '';

  rounds.forEach(r => {
    let list = SIMULATOR_DATA.filter(m => m.phase === r);
    let roundTitle = r === 'tercer-lugar' ? 'Tercer Lugar' : r === 'semis' ? 'Semifinal' : r;
    html += `<div class="bracket-column"><div class="bracket-column-title">${roundTitle}</div>`;
    
    list.forEach(m => {
      const isDone = m.homeScore !== null;
      const isHomeWin = isDone && m.homeScore > m.awayScore;
      const isAwayWin = isDone && m.awayScore > m.homeScore;
      const isPlaceholder = m.home.includes('Por definir') || m.home.includes('Ganador') || m.home.includes('Finalista') || m.home.includes('Perdedor');

      html += `
        <div class="bracket-match-node ${isPlaceholder ? 'unresolved-node' : ''}">
          <div class="node-info-row"><span class="node-match-id">M${m.id}</span><span>${m.date}</span></div>
          <div class="team-selectable-row ${isHomeWin ? 'selected-winner' : ''}" onclick="advanceQuinielaTeam(${m.id}, 'home')">
            <span>${m.flag} ${m.home}</span><span class="score-box-display">${m.homeScore !== null ? m.homeScore : '—'}</span>
          </div>
          <div class="team-selectable-row ${isAwayWin ? 'selected-winner' : ''}" onclick="advanceQuinielaTeam(${m.id}, 'away')">
            <span>${m.flagAway} ${m.away}</span><span class="score-box-display">${m.awayScore !== null ? m.awayScore : '—'}</span>
          </div>
        </div>`;
    });
    html += `</div>`;
  });
  container.innerHTML = html;
  container.style.transform = `scale(${globalZoom})`;
}

function advanceQuinielaTeam(matchId, side) {
  const m = SIMULATOR_DATA.find(x => x.id === matchId);
  if(!m || m.home.includes('Por definir') || m.home.includes('Ganador') || m.home.includes('Finalista') || m.home.includes('Perdedor')) return;

  m.homeScore = side === 'home' ? 1 : 0;
  m.awayScore = side === 'home' ? 0 : 1;

  const winnerName = side === 'home' ? m.home : m.away;
  const winnerFlag = side === 'home' ? m.flag : m.flagAway;
  const loserName = side === 'home' ? m.away : m.home;
  const loserFlag = side === 'home' ? m.flagAway : m.flag;

  if (m.phase === 'semis') {
    const finalMatch = SIMULATOR_DATA.find(x => x.phase === 'final');
    const thirdMatch = SIMULATOR_DATA.find(x => x.phase === 'tercer-lugar');
    if(m.id === 101) {
      finalMatch.home = winnerName; finalMatch.homeFlag = winnerFlag;
      thirdMatch.home = loserName; thirdMatch.flag = loserFlag;
    } else {
      finalMatch.away = winnerName; finalMatch.flagAway = winnerFlag;
      thirdMatch.away = loserName; thirdMatch.flagAway = loserFlag;
    }
  } else if(m.nextId) {
    const next = SIMULATOR_DATA.find(x => x.id === m.nextId);
    if(next) {
      if(m.slot === 'home') { next.home = winnerName; next.flag = winnerFlag; }
      else { next.away = winnerName; next.flagAway = winnerFlag; }
    }
  }
  render();
}

function resetCanvasView() { globalZoom = 0.65; render(); }

// CONTROLADOR DE PANEO EN DISPOSITIVOS TÁCTILES Y MOUSE MÓVIL
const trackScroll = document.getElementById('canvas-container-scroll');
let activeDrag = false; let startX, startY, sLeft, sTop;

const onStart = (e) => {
  activeDrag = true;
  const x = e.pageX || e.touches[0].pageX;
  const y = e.pageY || e.touches[0].pageY;
  startX = x - trackScroll.offsetLeft;
  startY = y - trackScroll.offsetTop;
  sLeft = trackScroll.scrollLeft; sTop = trackScroll.scrollTop;
};
trackScroll.addEventListener('mousedown', onStart);
trackScroll.addEventListener('touchstart', onStart);
trackScroll.addEventListener('mousemove', (e) => {
  if(!activeDrag) return;
  const x = e.pageX - trackScroll.offsetLeft;
  const y = e.pageY - trackScroll.offsetTop;
  trackScroll.scrollLeft = sLeft - (x - startX) * 1.5;
  trackScroll.scrollTop = sTop - (y - startY) * 1.5;
});
trackScroll.addEventListener('touchmove', (e) => {
  if(!activeDrag) return;
  const x = e.touches[0].pageX - trackScroll.offsetLeft;
  const y = e.touches[0].pageY - trackScroll.offsetTop;
  trackScroll.scrollLeft = sLeft - (x - startX) * 1.5;
  trackScroll.scrollTop = sTop - (y - startY) * 1.5;
});
window.addEventListener('mouseup', () => activeDrag = false);
trackScroll.addEventListener('touchend', () => activeDrag = false);

render();
</script>
</body>
</html>
