---
title: Tushar Arora
layout: default
---

<style>

/* =========================
   NEURO + BEHAVIOR SYSTEM (STABLE VERSION)
   ========================= */

:root {
  --bg: #070A12;
  --panel: rgba(17, 24, 39, 0.6);
  --text: #E5E7EB;
  --muted: #9CA3AF;

  --a1: #3B82F6;
  --a2: #22D3EE;
  --a3: #A78BFA;
}

html, body {
  margin: 0;
  padding: 0;
  background: var(--bg);
  color: var(--text);
  font-family: system-ui, -apple-system, Segoe UI, Roboto, sans-serif;
  overflow-x: hidden;
}

/* =========================
   BACKGROUND FIELD
   ========================= */

.bg {
  position: fixed;
  inset: 0;
  z-index: -3;
  background:
    radial-gradient(circle at 30% 40%, rgba(59,130,246,0.15), transparent 45%),
    radial-gradient(circle at 70% 60%, rgba(34,211,238,0.12), transparent 50%),
    radial-gradient(circle at 50% 30%, rgba(167,139,250,0.10), transparent 55%);
  animation: drift 18s ease-in-out infinite alternate;
}

@keyframes drift {
  0% { transform: scale(1); }
  100% { transform: scale(1.08); }
}

/* =========================
   BEHAVIOR CANVAS
   ========================= */

#canvas {
  position: fixed;
  inset: 0;
  z-index: -1;
  pointer-events: none;
}

/* =========================
   SIMPLE ARENA
   ========================= */

.arena {
  position: fixed;
  width: 520px;
  height: 520px;
  left: 50%;
  top: 55%;
  transform: translate(-50%, -50%);
  border-radius: 50%;
  border: 1px solid rgba(167,139,250,0.15);
  box-shadow: 0 0 80px rgba(34,211,238,0.06);
  z-index: -2;
}

/* =========================
   CONTENT
   ========================= */

.container {
  max-width: 900px;
  margin: auto;
  padding: 80px 20px;
}

h1 { font-size: 42px; }
p { color: var(--muted); line-height: 1.6; }

a { color: var(--a2); }

</style>

<!-- BACKGROUND LAYERS -->
<div class="bg"></div>
<div class="arena"></div>
<canvas id="canvas"></canvas>

<script>
/* =========================
   SAFE CANVAS INITIALIZATION
   (NO DOM ERRORS VERSION)
   ========================= */

const c = document.getElementById("canvas");
const ctx = c.getContext("2d");

function resize(){
  c.width = window.innerWidth;
  c.height = window.innerHeight;
}
resize();
window.addEventListener("resize", resize);

/* =========================
   COMPUTATIONAL MOUSE MODEL
   ========================= */

const m = {
  x: window.innerWidth * 0.5,
  y: window.innerHeight * 0.55,
  vx: 2,
  vy: 1
};

const target = {
  x: window.innerWidth * 0.65,
  y: window.innerHeight * 0.52
};

let path = [];

function loop(){

  ctx.clearRect(0,0,c.width,c.height);

  /* attraction (social/reward zone) */
  m.vx += (target.x - m.x) * 0.00002;
  m.vy += (target.y - m.y) * 0.00002;

  /* exploration noise */
  m.vx += (Math.random()-0.5)*0.3;
  m.vy += (Math.random()-0.5)*0.3;

  m.vx *= 0.96;
  m.vy *= 0.96;

  m.x += m.vx;
  m.y += m.vy;

  /* boundary (open field arena) */
  const cx = c.width/2;
  const cy = c.height*0.55;
  const r = 250;

  const d = Math.hypot(m.x-cx, m.y-cy);
  if(d>r){
    m.vx *= -0.7;
    m.vy *= -0.7;
  }

  path.push({x:m.x,y:m.y});
  if(path.length>120) path.shift();

  /* trajectory */
  ctx.beginPath();
  for(let i=0;i<path.length;i++){
    const p=path[i];
    if(i==0) ctx.moveTo(p.x,p.y);
    else ctx.lineTo(p.x,p.y);
  }

  ctx.strokeStyle="rgba(167,139,250,0.55)";
  ctx.lineWidth=2;
  ctx.stroke();

  /* agent */
  ctx.beginPath();
  ctx.arc(m.x,m.y,5,0,Math.PI*2);
  ctx.fillStyle="rgba(34,211,238,0.9)";
  ctx.fill();

  /* target */
  ctx.beginPath();
  ctx.arc(target.x,target.y,7,0,Math.PI*2);
  ctx.fillStyle="rgba(59,130,246,0.4)";
  ctx.fill();

  requestAnimationFrame(loop);
}

loop();
</script>

<div class="container">

# Tushar Arora, PhD  
Neuroscientist | Neural Circuits • Behavior • Computational Modeling  

I study how brain circuits generate social behavior using **in vivo recordings and computational behavioral analysis**.

---

## Research Focus
- Mouse behavior in open-field and social interaction paradigms  
- Computational modeling of decision-making and exploration  
- Neural circuit mechanisms underlying social reward  

---

## Contact
tushar.arora@mssm.edu  
LinkedIn | Google Scholar | X | Bluesky  

</div>
