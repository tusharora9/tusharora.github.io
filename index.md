---
title: Tushar Arora
layout: default
---

<style>

/* =========================
   NEURAL INTERFACE SYSTEM
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

/* ===== GLOBAL SAFE RESET ===== */

html, body {
  margin: 0;
  padding: 0;
  background: var(--bg);
  color: var(--text);
  font-family: Inter, system-ui, sans-serif;
  overflow-x: hidden;
}

/* ===== BACKGROUND LAYERS ===== */

.neural-bg {
  position: fixed;
  inset: 0;
  z-index: -3;
  overflow: hidden;
  background: radial-gradient(circle at 20% 20%, rgba(59,130,246,0.15), transparent 40%),
              radial-gradient(circle at 80% 40%, rgba(34,211,238,0.12), transparent 45%),
              radial-gradient(circle at 50% 80%, rgba(167,139,250,0.10), transparent 50%);
  animation: drift 18s ease-in-out infinite alternate;
}

@keyframes drift {
  0%   { transform: scale(1) translateY(0px); filter: hue-rotate(0deg); }
  100% { transform: scale(1.1) translateY(-20px); filter: hue-rotate(25deg); }
}

.particles {
  position: fixed;
  inset: 0;
  z-index: -2;
  pointer-events: none;
}

.particles span {
  position: absolute;
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: rgba(34,211,238,0.5);
  animation: float 12s linear infinite;
}

.particles span:nth-child(odd) {
  background: rgba(59,130,246,0.4);
}

@keyframes float {
  0%   { transform: translateY(100vh) scale(0.5); opacity: 0; }
  20%  { opacity: 1; }
  100% { transform: translateY(-10vh) scale(1); opacity: 0; }
}

.wave {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 200%;
  height: 200px;
  z-index: -1;
  opacity: 0.08;
  background: repeating-linear-gradient(
    90deg,
    rgba(34,211,238,0.5),
    rgba(59,130,246,0.5) 2px,
    transparent 4px,
    transparent 12px
  );
  animation: waveMove 8s linear infinite;
}

@keyframes waveMove {
  from { transform: translateX(0); }
  to   { transform: translateX(-50%); }
}

/* ===== SAFETY ===== */

.neural-bg, .particles, .wave {
  pointer-events: none;
}

/* ===== LAYOUT ===== */

.container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 80px 20px;
}

.hero {
  padding: 40px 0 20px;
}

/* ===== TYPOGRAPHY ===== */

h1 {
  font-size: 48px;
  letter-spacing: -0.03em;
}

h2 {
  margin-top: 40px;
  font-size: 26px;
}

p, li {
  color: var(--muted);
  line-height: 1.6;
}

/* ===== COMPONENTS ===== */

.card {
  background: var(--panel);
  border: 1px solid rgba(255,255,255,0.08);
  border-radius: 14px;
  padding: 18px;
  margin: 14px 0;
  backdrop-filter: blur(10px);
}

.signal {
  height: 3px;
  width: 60px;
  background: linear-gradient(90deg, var(--a1), var(--a2));
  margin: 10px 0 20px;
  border-radius: 10px;
}

/* ===== LINKS ===== */

a {
  color: var(--a2);
  text-decoration: none;
}

a:hover {
  opacity: 0.8;
}

</style>

<!-- BACKGROUND -->
<div class="neural-bg"></div>

<div class="particles">
  <span style="left:10%; animation-delay:0s;"></span>
  <span style="left:20%; animation-delay:2s;"></span>
  <span style="left:35%; animation-delay:4s;"></span>
  <span style="left:50%; animation-delay:1s;"></span>
  <span style="left:70%; animation-delay:3s;"></span>
  <span style="left:85%; animation-delay:5s;"></span>
</div>

<div class="wave"></div>

<!-- MAIN CONTENT -->
<div class="container">

<div class="hero">

# Tushar Arora, PhD
### Neuroscientist | Neural Circuits • Social Behavior • Neurotechnology

I study how neural circuits and neuromodulatory systems encode social behavior, with emphasis on sex-specific mechanisms and computational behavioral phenotyping.

Currently Postdoctoral Fellow at Icahn School of Medicine at Mount Sinai.

</div>

---

## Research

<div class="signal"></div>

<div class="card">
### Neural Circuits of Social Behavior

- Hypothalamic and limbic control of social behavior  
- Dopamine, serotonin & neuropeptide modulation  
- Sex-specific neural circuit dynamics  
</div>

<div class="card">
### Key Project

Neuropeptidergic modulation of serotonin & dopamine signaling in nucleus accumbens during social reward  
Conducted in Dr. Anita Autry’s lab at Albert Einstein College of Medicine.
</div>

---

## Current Position

- Postdoctoral Fellow — Mount Sinai (2025–Present)  
- Postdoctoral Fellow — Albert Einstein College of Medicine (2022–2025)  
- Research Fellow — NBRC India (2020–2021)

---

## Education

- PhD Neuroscience — NBRC India  
- M.Pharmacy Pharmacology — Jamia Hamdard  
- B.Pharmacy — Kurukshetra University  

---

<details>
<summary><b>Awards & Fellowships</b></summary>

- Jackson Labs NIH Course (2024)  
- Kavli Institute Summer School (2017)  
- NBRC Travel Fellowship (2017)  
- NET Qualified (2014)  

</details>

---

<details>
<summary><b>Teaching & Talks</b></summary>

- NYU SPS Invited Lecture (2024)  
- TA — Neuroscience Methods, Einstein (2024)

</details>

---

## Publications

<details>
<summary><b>Selected Papers</b></summary>

**Sex-specific hypothalamic projection activity drives caregiving** — Nature Communications 2025  
**Automated estrous cycle staging using ML detection** — 2025  
**Peptide modulation in Alzheimer’s model** — 2023  
**Synaptic signaling in trisomy hippocampus model** — 2020  

</details>

---

## Contact

Email: tushar.arora@mssm.edu  
[LinkedIn](https://www.linkedin.com/in/tushar-arora-a58b2b36/)  
[Google Scholar](https://scholar.google.com/citations?user=8hG0FHQAAAAJ&hl=en)  
[X (Twitter)](https://x.com/tusharora9)  
[Bluesky](https://bsky.app/profile/tusharora9.bsky.social)

</div>
