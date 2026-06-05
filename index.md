---
title: Tushar Arora
layout: default
---

<style>

/* =========================
   COMPUTATIONAL NEURO + BEHAVIOR SYSTEM
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

/* ===== GLOBAL ===== */

html, body {
  margin: 0;
  padding: 0;
  background: var(--bg);
  color: var(--text);
  font-family: Inter, system-ui, sans-serif;
  overflow-x: hidden;
}

/* =========================
   BACKGROUND LAYERS
   ========================= */

/* neural + computational field */
.bg-field {
  position: fixed;
  inset: 0;
  z-index: -3;
  background:
    radial-gradient(circle at 30% 40%, rgba(59,130,246,0.12), transparent 45%),
    radial-gradient(circle at 70% 60%, rgba(34,211,238,0.10), transparent 50%),
    radial-gradient(circle at 50% 30%, rgba(167,139,250,0.08), transparent 55%);
  animation: drift 20s ease-in-out infinite alternate;
}

@keyframes drift {
  0% { transform: scale(1) translateY(0px); }
  100% { transform: scale(1.08) translateY(-18px); }
}

/* scanline microscopy effect */
body::before {
  content: "";
  position: fixed;
  inset: 0;
  z-index: -2;
  pointer-events: none;
  background: repeating-linear-gradient(
    0deg,
    rgba(255,255,255,0.02),
    rgba(255,255,255,0.02) 1px,
    transparent 2px,
    transparent 6px
  );
  opacity: 0.25;
}

/* =========================
   BEHAVIORAL COMPUTATION LAYER
   ========================= */

#behaviorCanvas {
  position: fixed;
  inset: 0;
  z-index: -1;
  opacity: 0.38;
  pointer-events: none;
  mix-blend-mode: screen;
}

/* circular open-field arena */
.arena {
  position: fixed;
  width: 520px;
  height: 520px;
  left: 50%;
  top: 55%;
  transform: translate(-50%, -50%);
  border-radius: 50%;
  border: 1px solid rgba(167,139,250,0.15);
  box-shadow:
    0 0 80px rgba(34,211,238,0.05),
    inset 0 0 80px rgba(59,130,246,0.05);
  z-index: -2;
  pointer-events: none;
}

/* =========================
   UI LAYOUT
   ========================= */

.container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 80px 20px;
}

.hero {
  padding: 40px 0 20px;
}

h1 { font-size: 46px; }
h2 { margin-top: 40px; }

p, li {
  color: var(--muted);
  line-height: 1.6;
}

/* cards */
.card {
  background: var(--panel);
  border: 1px solid rgba(255,255,255,0.08);
  border-radius: 14px;
  padding: 18px;
  margin: 14px 0;
  backdrop-filter: blur(10px);
}

/* =========================
   LINKS
   ========================= */

a {
  color: var(--a2);
  text-decoration: none;
}

a:hover {
  opacity: 0.8;
}

</style>

<!-- BACKGROUND -->
<div class="bg-field"></div>
<div class="arena"></div>

<!-- BEHAVIOR CANVAS -->
<canvas id="behaviorCanvas"></canvas>

<script>
const canvas = document.getElementById("behaviorCanvas");
const ctx = canvas.getContext("2d");

function resize() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
}
resize();
window.addEventListener("resize", resize);

/* =========================
   COMPUTATIONAL MOUSE MODEL
   ========================= */

const mouse = {
  x: window.innerWidth * 0.5,
  y: window.innerHeight * 0.55,
  vx: 2,
  vy: 1.2
};

const target = {
  x: window.innerWidth * 0.65,
  y: window.innerHeight * 0.52
};

/* trajectory memory */
let path = [];

function draw() {

  ctx.clearRect(0, 0, canvas.width, canvas.height);

  /* attraction to "social zone" (computational behavioral model) */
  let dx = target.x - mouse.x;
  let dy = target.y - mouse.y;

  mouse.vx += dx * 0.00002;
  mouse.vy += dy * 0.00002;

  /* exploratory stochasticity (open field behavior) */
  mouse.vx += (Math.random() - 0.5) * 0.25;
  mouse.vy += (Math.random() - 0.5) * 0.25;

  mouse.vx *= 0.96;
  mouse.vy *= 0.96;

  mouse.x += mouse.vx;
  mouse.y += mouse.vy;

  /* arena boundary constraint */
  const cx = canvas.width / 2;
  const cy = canvas.height * 0.55;
  const r = 250;

  let dist = Math.hypot(mouse.x - cx, mouse.y - cy);
  if (dist > r) {
    mouse.vx *= -0.7;
    mouse.vy *= -0.7;
  }

  /* store trajectory */
  path.push({ x: mouse.x, y: mouse.y });
  if (path.length > 140) path.shift();

  /* =========================
     DRAW TRAJECTORY (behavioral trace)
     ========================= */

  ctx.beginPath();
  for (let i = 0; i < path.length; i++) {
    const p = path[i];
    if (i === 0) ctx.moveTo(p.x, p.y);
    else ctx.lineTo(p.x, p.y);
  }

  ctx.strokeStyle = "rgba(167,139,250,0.55)";
  ctx.lineWidth = 2;
  ctx.shadowBlur = 10;
  ctx.shadowColor = "rgba(167,139,250,0.3)";
  ctx.stroke();

  /* current position (tracked animal / DLC-like keypoint) */
  ctx.beginPath();
  ctx.arc(mouse.x, mouse.y, 5, 0, Math.PI * 2);
  ctx.fillStyle = "rgba(34,211,238,0.85)";
  ctx.fill();

  /* social target zone */
  ctx.beginPath();
  ctx.arc(target.x, target.y, 7, 0, Math.PI * 2);
  ctx.fillStyle = "rgba(59,130,246,0.35)";
  ctx.fill();

  requestAnimationFrame(draw);
}

draw();
</script>

<!-- MAIN CONTENT -->
<div class="container">

<div class="hero">

# Tushar Arora, PhD
### Neuroscientist | Neural Circuits • Behavior • Computational Modeling

I study how neural circuits generate **social behavior and decision-making**, integrating in vivo recordings, computational modeling, and automated behavioral quantification.

Currently Postdoctoral Fellow at Icahn School of Medicine at Mount Sinai.

</div>

---

## Research

<div class="card">
### Computational Behavioral Neuroscience

- Mouse open-field and social interaction paradigms  
- Quantitative trajectory analysis of behavior  
- Neural–behavior coupling frameworks  
</div>

<div class="card">
### Key Project

Neuropeptidergic modulation of dopamine and serotonin signaling during social reward behavior  
(Albert Einstein College of Medicine)
</div>

---

## Current Position
- Mount Sinai (2025–Present)  
- Albert Einstein College of Medicine (2022–2025)  
- NBRC India (2020–2021)

---

## Publications

Selected work includes:
- Social behavior neural circuits (Nature Communications 2025)  
- Behavioral tracking using ML-based quantification  
- Synaptic and molecular circuit mechanisms in disease models  

---

## Contact

Email: tushar.arora@mssm.edu  
LinkedIn | Google Scholar | X | Bluesky

</div>
