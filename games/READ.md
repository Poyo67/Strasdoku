[Grid-2.html](https://github.com/user-attachments/files/27441145/Grid-2.html)
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>TramDoku – Grille #2</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: 'Syne', sans-serif; background: #0f0f0f; color: #f0f0f0; min-height: 100vh; }


#tram-nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: #1a1a1a;
  border-bottom: 2px solid #ffcc00;
  padding: 10px 20px;
  font-family: 'Syne', sans-serif;
  position: sticky;
  top: 0;
  z-index: 50;
}
.nav-btn {
  color: #ffcc00;
  text-decoration: none;
  font-size: 14px;
  font-weight: 700;
  padding: 6px 14px;
  border: 1px solid #333;
  border-radius: 6px;
  background: #111;
  transition: all .15s;
}
.nav-btn:hover { background: #ffcc00; color: #000; border-color: #ffcc00; }
.nav-home {
  font-size: 20px;
  text-decoration: none;
  opacity: 0.8;
  transition: opacity .15s;
}
.nav-home:hover { opacity: 1; }


.game-wrap { padding: 24px 20px 60px; max-width: 700px; margin: 0 auto; }

h1 { font-size: 1.6rem; font-weight: 800; margin-bottom: 4px; }
.grid-label {
  font-family: 'DM Mono', monospace;
  font-size: 12px;
  color: #888;
  letter-spacing: .08em;
  margin-bottom: 20px;
}

table { border-collapse: collapse; width: 100%; margin: 20px 0; }
th, td { border: 1px solid #2e2e2e; padding: 8px 6px; }
th { background: #1a1a1a; color: #ffcc00; font-size: 13px; }
td { background: #161616; }
input {
  width: 100%;
  background: transparent;
  border: none;
  outline: none;
  color: #f0f0f0;
  font-family: 'DM Mono', monospace;
  font-size: 13px;
  text-align: center;
  padding: 4px 0;
}
.ok  { background: #1b3a1f !important; }
.ko  { background: #3a1b1b !important; }
.dup { background: #3a2d10 !important; }

.bars { margin: 16px 0; display: flex; flex-direction: column; gap: 8px; }
.barre-wrap { display: flex; align-items: center; gap: 10px; }
.barre-label { font-family: 'DM Mono', monospace; font-size: 12px; color: #888; width: 100px; text-align: right; }
.barre { flex: 1; height: 16px; background: #1a1a1a; border: 1px solid #2e2e2e; border-radius: 4px; overflow: hidden; }
.progress-score { height: 100%; background: #ffcc00; width: 0%; transition: width .4s; }
.progress-orig  { height: 100%; background: #7c4dff; width: 0%; transition: width .4s; }
.barre-val { font-family: 'DM Mono', monospace; font-size: 12px; width: 80px; color: #aaa; }

.btn-row { display: flex; gap: 10px; margin: 16px 0; flex-wrap: wrap; }
button {
  font-family: 'Syne', sans-serif;
  font-weight: 700;
  font-size: 14px;
  padding: 10px 18px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: all .15s;
}
.btn-verify { background: #ffcc00; color: #000; }
.btn-verify:hover { background: #e6b800; }
.btn-sol { background: #1a1a1a; color: #f0f0f0; border: 1px solid #2e2e2e; }
.btn-sol:hover { border-color: #555; }

#bonusZone {
  display: none;
  border: 2px dashed #ffcc00;
  background: #1a1700;
  padding: 12px;
  border-radius: 8px;
  margin: 16px 0;
  text-align: center;
}
#bonusZone input {
  width: 220px;
  background: #111;
  border: 1px solid #333;
  border-radius: 6px;
  padding: 6px 10px;
  margin-top: 8px;
  display: block;
  margin: 8px auto 0;
}

.victoire {
  display: none;
  font-size: 18px;
  font-weight: 800;
  color: #ffcc00;
  margin: 12px 0;
  text-align: center;
  letter-spacing: .05em;
}

#solutions {
  display: none;
  margin-top: 10px;
}
#solutions table th { color: #7c4dff; }
#solutions table td { font-family: 'DM Mono', monospace; font-size: 12px; color: #aaa; }

.orig-badge {
  display: inline-block;
  font-size: 10px;
  background: #1c1030;
  color: #7c4dff;
  border-radius: 6px;
  padding: 1px 5px;
  margin-left: 4px;
}

.regles {
  font-size: 12px;
  color: #555;
  margin-top: 28px;
  font-family: 'DM Mono', monospace;
  line-height: 1.8;
  border-top: 1px solid #1e1e1e;
  padding-top: 16px;
}
</style>
</head>
<body>


<nav id="tram-nav">
  <a href="index.html" class="nav-btn" id="nav-prev">← Accueil</a>
  <a href="index.html" class="nav-home" title="Accueil">🏠</a>
  <a href="Strasdoku-3.html" class="nav-btn" id="nav-next">Grille #3 →</a>
</nav>

<div class="game-wrap">
<h1>🚋 TramDoku</h1>
<div class="grid-label">GRILLE #2</div>

<div class="bars">
  <div class="barre-wrap">
    <span class="barre-label">🎯 Score</span>
    <div class="barre"><div id="progress-score" class="progress-score"></div></div>
    <span class="barre-val"><span id="score">0</span> / <span id="scoreMax">900</span></span>
  </div>
  <div class="barre-wrap">
    <span class="barre-label">✨ Originalité</span>
    <div class="barre"><div id="progress-orig" class="progress-orig"></div></div>
    <span class="barre-val"><span id="origScore">0</span> / 505</span>
  </div>
</div>

<div id="jeu"></div>

<div class="btn-row">
  <button class="btn-verify" onclick="verifier()">✅ Vérifier</button>
  <button class="btn-sol" onclick="toggleSolutions()">📋 Solutions</button>
</div>

<div id="solutions"></div>

<div id="bonusZone">
  <strong>⭐ Case bonus</strong><br>
  <span id="bonusLabel"></span>
  <input id="bonusInput" placeholder="Station…" onkeydown="if(event.key==='Enter') verifierBonus()">
  <button class="btn-verify" style="margin-top:8px" onclick="verifierBonus()">Valider</button>
</div>

<div id="victoire" class="victoire">🎉 Score maximum atteint !</div>

<div class="regles">
  • Chaque case = une station de tram de Strasbourg.<br>
  • Ligne = contrainte horizontale · Colonne = verticale.<br>
  • Une case peut avoir plusieurs solutions : une seule suffit.<br>
  • Une station ne peut être utilisée qu'une seule fois.<br>
  • 900 points → case bonus débloquée (1000 max).<br>
  • La barre violette mesure l'originalité de tes réponses.
</div>
</div>

<script>
const data = {"cols":["Tram A","Contient un prénom","Ligne verte"],"rows":["Tram B","Terminus","Commence par une voyelle"],"solutions":{"0,0":[{"nom":"Homme de fer","originalite":10}],"0,1":[{"nom":"Martin Schongauer","originalite":80}],"0,2":[{"nom":"Broglie","originalite":15}],"1,0":[{"nom":"Graffenstaden","originalite":70}],"1,1":[{"nom":"Wolfisheim Henri Rendu","originalite":90}],"1,2":[{"nom":"Poteries","originalite":60}],"2,0":[{"nom":"Illkirch Lixenbuhl","originalite":75}],"2,1":[{"nom":"Emile Mathis","originalite":85}],"2,2":[{"nom":"Université","originalite":20}]},"bonus":{"label":"Station emblématique de Strasbourg","points":100,"solutions":["Homme de fer","Broglie","Republique"]}};
const ORIG_MAX = 505;
let scoreMax = 900;
let scoreBase = 0;
let origBase = 0;
let bonusUnlocked = false;
let bonusValidated = false;

function n(t) {
  return t.toLowerCase().normalize("NFD")
    .replace(/[\u0300-\u036f]/g, "")
    .replace(/\s+/g, " ")
    .trim();
}

function parseSol(s) {
  if (typeof s === "object") return { nom: s.nom, orig: s.originalite || 0 };
  return { nom: s, orig: 0 };
}

function afficher() {
  let h = "<table><tr><th></th>";
  data.cols.forEach(c => h += "<th>" + c + "</th>");
  h += "</tr>";
  data.rows.forEach((r,i) => {
    h += "<tr><th>" + r + "</th>";
    data.cols.forEach((_,j) => h += "<td><input data-k='"+i+","+j+"'></td>");
    h += "</tr>";
  });
  h += "</table>";
  document.getElementById("jeu").innerHTML = h;
}

function updateBars(score, orig) {
  document.getElementById("score").textContent = score;
  document.getElementById("origScore").textContent = orig;
  document.getElementById("progress-score").style.width = (score / scoreMax * 100) + "%";
  document.getElementById("progress-orig").style.width = ORIG_MAX > 0 ? (orig / ORIG_MAX * 100) + "%" : "0%";
}

function verifier() {
  let score = 0, orig = 0, used = {}, doublon = false;
  document.getElementById("victoire").style.display = "none";

  document.querySelectorAll("input[data-k]").forEach(inp => {
    inp.parentElement.className = "";
    const v = n(inp.value);
    if (!v) return;
    if (used[v]) { inp.parentElement.className = "dup"; doublon = true; return; }
    used[v] = true;
    const sols = (data.solutions[inp.dataset.k] || []).map(parseSol);
    const match = sols.find(s => n(s.nom) === v);
    if (match) { inp.parentElement.className = "ok"; score += 100; orig += match.orig; }
    else inp.parentElement.className = "ko";
  });

  if (score === 900 && !doublon && data.bonus && !bonusUnlocked) {
    bonusUnlocked = true;
    scoreMax = 900 + data.bonus.points;
    document.getElementById("scoreMax").textContent = scoreMax;
    document.getElementById("bonusZone").style.display = "block";
    document.getElementById("bonusLabel").textContent = data.bonus.label;
  }

  scoreBase = score;
  origBase = orig;
  updateBars(score + (bonusValidated ? data.bonus.points : 0), orig);
}

function verifierBonus() {
  if (!bonusUnlocked) return;
  const input = document.getElementById("bonusInput");
  const v = n(input.value);
  input.className = "";
  if (!v) return;
  const sols = (data.bonus.solutions || []).map(n);
  if (sols.includes(v)) {
    bonusValidated = true;
    input.style.background = "#1b3a1f";
    document.getElementById("victoire").style.display = "block";
    updateBars(scoreBase + data.bonus.points, origBase);
  } else {
    bonusValidated = false;
    input.style.background = "#3a1b1b";
    document.getElementById("victoire").style.display = "none";
    updateBars(scoreBase, origBase);
  }
}

function toggleSolutions() {
  const d = document.getElementById("solutions");
  if (d.style.display === "block") { d.style.display = "none"; return; }
  let h = "<table><tr><th></th>";
  data.cols.forEach(c => h += "<th>" + c + "</th>");
  h += "</tr>";
  data.rows.forEach((r,i) => {
    h += "<tr><th>" + r + "</th>";
    data.cols.forEach((_,j) => {
      const sols = (data.solutions[i+","+j] || []).map(parseSol);
      h += "<td>" + sols.map(s =>
        s.nom + (s.orig > 0 ? '<span class="orig-badge">✨' + s.orig + '</span>' : '')
      ).join("<br><em>ou</em><br>") + "</td>";
    });
    h += "</tr>";
  });
  h += "</table>";
  d.innerHTML = h;
  d.style.display = "block";
}
  [Grid-5.html](https://github.com/user-attachments/files/27441157/Grid-5.html)<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>TramDoku</title>
<style>
body { font-family: Arial, sans-serif; text-align: center; padding: 20px; background:#fafafa; }
table { border-collapse: collapse; margin: 20px auto; }
th, td { border: 1px solid #444; padding: 8px; }
th { background: #eee; }
input { width: 100%; text-align: center; }

.ok  { background: #c8f7c5; }
.ko  { background: #f7c5c5; }
.dup { background: #ffe0b2; }

.barre-wrap { width: 340px; margin: 5px auto; display: flex; align-items: center; gap: 8px; }
.barre-label { font-size: 13px; width: 90px; text-align: right; white-space: nowrap; }
.barre { flex: 1; height: 18px; border: 1px solid #999; background: #e8e8e8; border-radius: 4px; overflow: hidden; }
.progress-score { height: 100%; background: #4caf50; width: 0%; transition: width .3s; }
.progress-orig  { height: 100%; background: #7c4dff; width: 0%; transition: width .3s; }
.barre-val { font-size: 13px; width: 70px; text-align: left; }

#bonusZone {
  display: none;
  border: 2px dashed #fbc02d;
  background: #fff8e1;
  padding: 8px;
  width: 280px;
  margin: 15px auto;
}

.regles { font-size: 12px; color: #666; margin-top: 25px; }
.victoire { font-size: 20px; color: #2e7d32; font-weight: bold; display: none; margin: 10px 0; }

.orig-badge {
  display: inline-block;
  font-size: 11px;
  background: #ede7f6;
  color: #5e35b1;
  border-radius: 8px;
  padding: 1px 6px;
  margin-left: 4px;
}
</style>
</head>
<body>

<h1>🚋 TramDoku</h1>

<div class="barre-wrap">
  <span class="barre-label">🎯 Score</span>
  <div class="barre"><div id="progress-score" class="progress-score"></div></div>
  <span class="barre-val"><span id="score">0</span> / <span id="scoreMax">900</span></span>
</div>
<div class="barre-wrap">
  <span class="barre-label">✨ Originalité</span>
  <div class="barre"><div id="progress-orig" class="progress-orig"></div></div>
  <span class="barre-val"><span id="origScore">0</span> / 780</span>
</div>

<div id="jeu"></div>

<button onclick="verifier()">✅ Vérifier</button>
<button onclick="toggleSolutions()">📋 Solutions</button>

<div id="solutions" style="display:none;"></div>

<div id="bonusZone">
  <strong>⭐ Case bonus</strong><br>
  <span id="bonusLabel"></span><br>
  <input id="bonusInput" placeholder="Station…" onkeydown="if(event.key==='Enter') verifierBonus()">
  <button onclick="verifierBonus()">✅ Valider le bonus</button>
</div>

<div id="victoire" class="victoire">🎉 Bravo ! Score maximum atteint 🎉</div>
<div class="regles">
<strong>Règles du jeu</strong><br>
• Chaque case doit contenir une station de tram de Strasbourg.<br>
• Ligne = contrainte horizontale, colonne = verticale.<br>
• Une case peut avoir plusieurs solutions : une seule suffit.<br>
• Une station ne peut être utilisée qu'une seule fois.<br>
• 900 points → déblocage de la case bonus (1000 max).<br>
• La barre violette mesure l'originalité de tes réponses.
</div>

<script>
const data = {"cols":["Entre république et landsberg","contient un nom de ville","Contient 'me'"],"rows":["N'est pas un terminus","2 correspondances ","Plus loin de 3 stations de hdf"],"solutions":{"0,0":[{"nom":"Gallia","originalite":60},{"nom":"université","originalite":40},{"nom":"observatoire","originalite":50},{"nom":"esplanade","originalite":75},{"nom":"Winston churchill","originalite":100}],"0,1":[{"nom":"Kehl bahnhof","originalite":50},{"nom":"Parc d'activités d'eckobolsheim zénith","originalite":65},{"nom":"Hohberg","originalite":100},{"nom":"Saint-florent","originalite":100},{"nom":"Illkirch Lixenbuhl","originalite":75},{"nom":"Faubourg de Saverne","originalite":75},{"nom":"Lingolsheim alouettes","originalite":85},{"nom":"Ostwald hotel de ville","originalite":80},{"nom":"Phalsbourg","originalite":100},{"nom":"Copenhague","originalite":100},{"nom":"Londres","originalite":100},{"nom":"Vienne","originalite":100}],"0,2":[{"nom":"Homme de fer","originalite":1},{"nom":"Elmerforst","originalite":100},{"nom":"Krimmeri stade de la meinau","originalite":60},{"nom":"Graviere stade de la meinau","originalite":70},{"nom":"melanie","originalite":75},{"nom":"Droits de l'homme","originalite":95},{"nom":"Clemenceau","originalite":100}],"1,0":[{"nom":"Esplanade","originalite":5}],"1,1":[{"nom":"Campus d'illkirch","originalite":25},{"nom":"Saint-florent","originalite":95}],"1,2":[{"nom":"Krimmeri stade de la meinau","originalite":60},{"nom":"Parlement européen","originalite":80}],"2,0":[{"nom":"université","originalite":40},{"nom":"observatoire","originalite":50},{"nom":"esplanade","originalite":75},{"nom":"Winston churchill","originalite":100}],"2,1":[{"nom":"Kehl bahnhof","originalite":50},{"nom":"Parc d'activités d'eckobolsheim zénith","originalite":65},{"nom":"Hohberg","originalite":100},{"nom":"Saint-florent","originalite":100},{"nom":"Illkirch Lixenbuhl","originalite":75},{"nom":"Faubourg de Saverne","originalite":75},{"nom":"Lingolsheim alouettes","originalite":85},{"nom":"Ostwald hotel de ville","originalite":80},{"nom":"Phalsbourg","originalite":100},{"nom":"Copenhague","originalite":100},{"nom":"Londres","originalite":100},{"nom":"Vienne","originalite":100},{"nom":"Wolfisheim Henri rendu","originalite":50},{"nom":"Hoenheim gare","originalite":50},{"nom":"Rotterdam","originalité":100},{"nom":"Kehl Rathaus","originalite":30},{"nom":"Campus d'illkirch","originalite":30},{"nom":"Lingolsheim Tiergaertel","originalite":45}],"2,2":[{"nom":"Graviere stade de la meinau","originalite":50},{"nom":"Krimmeri stade de la meinau ","originalite":25},{"nom":"Parlement européen","originalite":35},{"nom":"Mélanie","originalite":100},{"nom":"Chambre de métiers","originalite":100},{"nom":"Clemenceau","originalite":100},{"nom":"Elmerforst","originalite":100}]},"bonus":{"label":"Station emblématique de Strasbourg","points":100,"solutions":["Homme de fer","Broglie","Republique"]}};
const ORIG_MAX = 780;
let scoreMax = 900;
let scoreBase = 0;
let origBase = 0;
let bonusUnlocked = false;
let bonusValidated = false;

function n(t) {
  return t.toLowerCase().normalize("NFD")
    .replace(/[\u0300-\u036f]/g, "")
    .replace(/\s+/g, " ")
    .trim();
}

function parseSol(s) {
  if (typeof s === "object") return { nom: s.nom, orig: s.originalite || 0 };
  return { nom: s, orig: 0 };
}

function afficher() {
  let h = "<table><tr><th></th>";
  data.cols.forEach(c => h += "<th>" + c + "</th>");
  h += "</tr>";
  data.rows.forEach((r,i) => {
    h += "<tr><th>" + r + "</th>";
    data.cols.forEach((_,j) => h += "<td><input data-k='"+i+","+j+"'></td>");
    h += "</tr>";
  });
  h += "</table>";
  document.getElementById("jeu").innerHTML = h;
}

function updateBars(score, orig) {
  document.getElementById("score").textContent = score;
  document.getElementById("origScore").textContent = orig;
  document.getElementById("progress-score").style.width = (score / scoreMax * 100) + "%";
  document.getElementById("progress-orig").style.width = ORIG_MAX > 0 ? (orig / ORIG_MAX * 100) + "%" : "0%";
}

function verifier() {
  let score = 0;
  let orig = 0;
  let used = {};
  let doublon = false;
  document.getElementById("victoire").style.display = "none";

  document.querySelectorAll("input[data-k]").forEach(inp => {
    inp.className = "";
    const v = n(inp.value);
    if (!v) return;
    if (used[v]) { inp.className = "dup"; doublon = true; return; }
    used[v] = true;
    const sols = (data.solutions[inp.dataset.k] || []).map(parseSol);
    const match = sols.find(s => n(s.nom) === v);
    if (match) { inp.className = "ok"; score += 100; orig += match.orig; }
    else inp.className = "ko";
  });

  if (score === 900 && !doublon && data.bonus && !bonusUnlocked) {
    bonusUnlocked = true;
    scoreMax = 900 + data.bonus.points;
    document.getElementById("scoreMax").textContent = scoreMax;
    document.getElementById("bonusZone").style.display = "block";
    document.getElementById("bonusLabel").textContent = data.bonus.label;
  }

  scoreBase = score;
  origBase = orig;
  updateBars(score + (bonusValidated ? data.bonus.points : 0), orig);
}

function verifierBonus() {
  if (!bonusUnlocked) return;
  const input = document.getElementById("bonusInput");
  const v = n(input.value);
  input.className = "";
  if (!v) return;
  const sols = (data.bonus.solutions || []).map(n);
  if (sols.includes(v)) {
    bonusValidated = true;
    input.className = "ok";
    document.getElementById("victoire").style.display = "block";
    updateBars(scoreBase + data.bonus.points, origBase);
  } else {
    bonusValidated = false;
    input.className = "ko";
    document.getElementById("victoire").style.display = "none";
    updateBars(scoreBase, origBase);
  }
}

function toggleSolutions() {
  const d = document.getElementById("solutions");
  if (d.style.display === "block") { d.style.display = "none"; return; }
  let h = "<table><tr><th></th>";
  data.cols.forEach(c => h += "<th>" + c + "</th>");
  h += "</tr>";
  data.rows.forEach((r,i) => {
    h += "<tr><th>" + r + "</th>";
    data.cols.forEach((_,j) => {
      const sols = (data.solutions[i+","+j] || []).map(parseSol);
      h += "<td>" + sols.map(s =>
        s.nom + (s.orig > 0 ? '<span class="orig-badge">✨ ' + s.orig + '</span>' : '')
      ).join("<br><em>ou</em><br>") + "</td>";
    });
    h += "</tr>";
  });
  h += "</table>";
  d.innerHTML = h;
  d.style.display = "block";
}

afficher();
</script>

</body>
</html>


afficher();
</script>
</body>
</html>
