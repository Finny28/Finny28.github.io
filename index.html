<!DOCTYPE html>
<html lang="it">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Scoreboard Overlay - Casa / Fuori</title>
<style>
  :root{
    --text: #fff;
    --muted: rgba(255,255,255,0.6);
    --font: "Segoe UI", Roboto, Arial, sans-serif;
  }

  html,body{
    height:100%;
    margin:0;
    background:rgba(0,0,0,0);
    font-family:var(--font);
    color:var(--text);
  }

  .wrap {
    display:flex;
    justify-content:center;
    align-items:center;
    height:100%;
  }

  .scoreboard {
    display:flex;
    border: 4px solid black; /* ✅ Bordo nero esterno */
    border-radius:14px;
    overflow:hidden;
    position:relative;
  }

  /* ✅ Linea nera centrale più spessa */
  .scoreboard::before {
    content:"";
    position:absolute;
    top:0;
    bottom:0;
    left:50%;
    width:6px;
    background:black;
    transform:translateX(-50%);
    z-index:2;
  }

  /* ✅ QUI PUOI CAMBIARE I COLORI RGB DELLE DUE METÀ */
  .team.home {
    background-color: rgb(255, 140, 0); /* Arancione */
  }
  .team.away {
    background-color: rgb(0, 102, 204); /* Blu */
  }

  .team {
    flex:1;
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    padding:20px;
    min-width:240px;
    position:relative;
    z-index:3; /* sopra la linea centrale */
  }

  .name {
    font-size:28px;
    font-weight:700;
    margin-bottom:6px;
    outline:none;
    min-height:34px;
  }

  .points {
    font-size:72px;
    font-weight:900;
    line-height:1;
  }

  .sets {
    margin-top:6px;
    font-size:18px;
    color:var(--muted);
  }

  .serve-indicator {
    font-size:28px;
    margin-top:8px;
    opacity:0;
    transition:opacity .15s;
  }
  .serve-indicator.active{ opacity:1; }

  /* Controls */
  .controls {
    position:fixed;
    bottom:18px;
    left:50%;
    transform:translateX(-50%);
    display:flex;
    flex-wrap:wrap;
    gap:8px;
    padding:10px 12px;
    background: rgba(0,0,0,0.5);
    border-radius:10px;
    z-index:9999;
  }

  .controls button {
    padding:8px 10px;
    border-radius:8px;
    border:1px solid rgba(255,255,255,0.06);
    background:transparent;
    color:var(--text);
    cursor:pointer;
    font-weight:700;
  }

  .controls button:hover {
    background:rgba(255,255,255,0.04);
  }

  @media (max-width:700px){
    .scoreboard{flex-direction:column;}
    .scoreboard::before{display:none;} /* niente linea centrale in verticale */
    .points{font-size:48px;}
  }
</style>
</head>
<body>
  <div class="wrap">
    <div class="scoreboard" role="region" aria-label="Scoreboard">
      <div class="team home" id="homeTeam">
        <div class="name" id="homeName" contenteditable="true" spellcheck="false">Casa</div>
        <div class="points" id="homePoints">0</div>
        <div class="sets" id="homeSets">Set: 0</div>
        <div class="serve-indicator" id="homeServe">🏐</div>
      </div>

      <div class="team away" id="awayTeam">
        <div class="name" id="awayName" contenteditable="true" spellcheck="false">Fuori</div>
        <div class="points" id="awayPoints">0</div>
        <div class="sets" id="awaySets">Set: 0</div>
        <div class="serve-indicator" id="awayServe">🏐</div>
      </div>
    </div>
  </div>

  <div class="controls" id="controls">
    <button id="incHomePoint">+ Punto Casa</button>
    <button id="decHomePoint">- Punto Casa</button>
    <button id="incAwayPoint">+ Punto Fuori</button>
    <button id="decAwayPoint">- Punto Fuori</button>

    <button id="incHomeSet">+ Set Casa</button>
    <button id="decHomeSet">- Set Casa</button>
    <button id="incAwaySet">+ Set Fuori</button>
    <button id="decAwaySet">- Set Fuori</button>

    <button id="toggleServe">Cambia Servizio</button>
    <button id="resetBtn">Reset</button>
  </div>

<script>
/* Stato e riferimenti DOM */
const STATE_KEY = "scoreboard_casa_fuori_v1";
let state = {
  homeName: "Casa",
  awayName: "Fuori",
  homePoints: 0,
  awayPoints: 0,
  homeSets: 0,
  awaySets: 0,
  serving: "home"
};

const els = {
  homeName: document.getElementById("homeName"),
  awayName: document.getElementById("awayName"),
  homePoints: document.getElementById("homePoints"),
  awayPoints: document.getElementById("awayPoints"),
  homeSets: document.getElementById("homeSets"),
  awaySets: document.getElementById("awaySets"),
  homeServe: document.getElementById("homeServe"),
  awayServe: document.getElementById("awayServe"),
};

/* Carica stato se presente */
(function load(){
  try {
    const raw = localStorage.getItem(STATE_KEY);
    if(raw){
      const parsed = JSON.parse(raw);
      state = Object.assign(state, parsed);
    }
  } catch(e){
    console.warn("Impossibile caricare stato:", e);
  }
})();

function save(){
  try { localStorage.setItem(STATE_KEY, JSON.stringify(state)); } catch(e){ console.warn(e); }
}

/* Rendering */
function render(){
  els.homeName.textContent = state.homeName;
  els.awayName.textContent = state.awayName;
  els.homePoints.textContent = String(state.homePoints);
  els.awayPoints.textContent = String(state.awayPoints);
  els.homeSets.textContent = "Set: " + state.homeSets;
  els.awaySets.textContent = "Set: " + state.awaySets;

  els.homeServe.classList.toggle("active", state.serving === "home");
  els.awayServe.classList.toggle("active", state.serving === "away");

  save();
}
render();

/* Funzioni di mutazione */
function incPoint(team){
  if(team === "home") state.homePoints++;
  else state.awayPoints++;
  render();
}
function decPoint(team){
  if(team === "home") state.homePoints = Math.max(0, state.homePoints - 1);
  else state.awayPoints = Math.max(0, state.awayPoints - 1);
  render();
}
function incSet(team){
  if(team === "home") state.homeSets++;
  else state.awaySets++;
  render();
}
function decSet(team){
  if(team === "home") state.homeSets = Math.max(0, state.homeSets - 1);
  else state.awaySets = Math.max(0, state.awaySets - 1);
  render();
}
function toggleServe(){
  state.serving = (state.serving === "home") ? "away" : "home";
  render();
}
function resetAll(){
  if(!confirm("Reset completo? (nomi resteranno)")) return;
  state.homePoints = 0; state.awayPoints = 0;
  state.homeSets = 0; state.awaySets = 0;
  state.serving = "home";
  render();
}

/* Collego i pulsanti via JS */
document.getElementById("incHomePoint").addEventListener("click", ()=> incPoint("home"));
document.getElementById("decHomePoint").addEventListener("click", ()=> decPoint("home"));
document.getElementById("incAwayPoint").addEventListener("click", ()=> incPoint("away"));
document.getElementById("decAwayPoint").addEventListener("click", ()=> decPoint("away"));

document.getElementById("incHomeSet").addEventListener("click", ()=> incSet("home"));
document.getElementById("decHomeSet").addEventListener("click", ()=> decSet("home"));
document.getElementById("incAwaySet").addEventListener("click", ()=> incSet("away"));
document.getElementById("decAwaySet").addEventListener("click", ()=> decSet("away"));

document.getElementById("toggleServe").addEventListener("click", toggleServe);
document.getElementById("resetBtn").addEventListener("click", resetAll);

/* Aggiorna stato quando si editano i nomi */
function setupEditable(el, key){
  el.addEventListener("input", ()=> {
    state[key] = el.textContent.trim() || (key==="homeName" ? "Casa" : "Fuori");
    save();
  });
  el.addEventListener("blur", ()=> { el.textContent = state[key]; save(); });
}
setupEditable(els.homeName, "homeName");
setupEditable(els.awayName, "awayName");

/* Scorciatoie da tastiera */
window.addEventListener("keydown", (e)=>{
  const active = document.activeElement;
  const editing = active && (active.id === "homeName" || active.id === "awayName");
  if(editing) return;

  if(e.key === "q" || e.key === "Q"){ incPoint("home"); e.preventDefault(); }
  if(e.key === "a" || e.key === "A"){ decPoint("home"); e.preventDefault(); }
  if(e.key === "p" || e.key === "P"){ incPoint("away"); e.preventDefault(); }
  if(e.key === "l" || e.key === "L"){ decPoint("away"); e.preventDefault(); }
  if(e.key === "s" || e.key === "S"){ toggleServe(); e.preventDefault(); }
  if(e.key === "r" || e.key === "R"){ resetAll(); e.preventDefault(); }
});

render();
</script>
</body>
</html>
