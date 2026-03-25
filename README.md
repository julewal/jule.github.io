*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { font-size: 16px; }

body {
  font-family: 'DM Sans', sans-serif;
  background: var(--sand);
  color: var(--ink);
  -webkit-font-smoothing: antialiased;
}

.material-symbols-outlined {
  font-variation-settings: 'FILL' 0, 'wght' 400, 'GRAD' 0, 'opsz' 24;
  vertical-align: middle;
  font-size: 1.1rem;
}

/* ─── Nav ─── */
nav {
  position: fixed; top: 0; width: 100%; z-index: 100;
  background: rgba(248, 246, 241, 0.88);
  backdrop-filter: blur(18px);
  -webkit-backdrop-filter: blur(18px);
  border-bottom: 1px solid rgba(221,227,232,0.5);
}
.nav-inner {
  max-width: 1100px; margin: 0 auto;
  padding: 0.9rem 2rem;
  display: flex; justify-content: space-between; align-items: center;
}
.nav-brand {
  font-family: 'Manrope', sans-serif;
  font-weight: 900; font-size: 1.1rem;
  color: var(--teal-dark); letter-spacing: -0.03em;
}
.nav-links {
  display: flex; gap: 2rem; align-items: center; list-style: none;
}
.nav-links a {
  font-size: 0.78rem; font-weight: 600;
  text-transform: uppercase; letter-spacing: 0.1em;
  color: var(--muted); text-decoration: none;
  transition: color 0.2s;
  font-family: 'Manrope', sans-serif;
}
.nav-links a:hover { color: var(--teal); }

/* ─── Hero ─── */
.hero {
  min-height: 100vh;
  display: flex; align-items: center;
  padding: 7rem 2rem 4rem;
  position: relative; overflow: hidden;
}
.hero::before {
  content: '';
  position: absolute; top: -20%; right: -10%;
  width: 55vw; height: 90vh;
  background: radial-gradient(ellipse at 70% 30%, rgba(26,107,135,0.08) 0%, transparent 65%);
  pointer-events: none;
}
.hero-inner {
  max-width: 1100px; margin: 0 auto; width: 100%;
  display: grid; grid-template-columns: 1fr 1fr; gap: 5rem; align-items: center;
}
.hero-badge {
  display: inline-flex; align-items: center; gap: 0.4rem;
  background: var(--rose-light); color: var(--rose);
  font-size: 0.65rem; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.15em;
  padding: 0.4rem 0.9rem; border-radius: 999px;
  margin-bottom: 1.5rem;
  font-family: 'Manrope', sans-serif;
}
.hero h1 {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(3rem, 5.5vw, 5rem);
  line-height: 1.05;
  color: var(--teal-dark);
  margin-bottom: 1.25rem;
  letter-spacing: -0.02em;
}
.hero h1 em { color: var(--rose); font-style: italic; }
.hero-sub {
  font-size: 1.05rem; color: var(--muted);
  line-height: 1.75; max-width: 480px;
  margin-bottom: 2.25rem;
}
.hero-ctas { display: flex; gap: 1rem; flex-wrap: wrap; }
.btn-primary {
  background: var(--teal-dark); color: #fff;
  padding: 0.85rem 2rem; border-radius: 0.6rem;
  font-weight: 700; font-size: 0.82rem;
  text-transform: uppercase; letter-spacing: 0.1em;
  text-decoration: none;
  font-family: 'Manrope', sans-serif;
  transition: background 0.2s, transform 0.12s;
  display: inline-flex; align-items: center; gap: 0.4rem;
}
.btn-primary:hover { background: var(--teal-deeper); transform: translateY(-2px); }
.btn-ghost {
  background: transparent; color: var(--teal-dark);
  padding: 0.85rem 2rem; border-radius: 0.6rem;
  font-weight: 700; font-size: 0.82rem;
  text-transform: uppercase; letter-spacing: 0.1em;
  text-decoration: none;
  font-family: 'Manrope', sans-serif;
  border: 1.5px solid var(--teal-dark);
  transition: background 0.2s, transform 0.12s;
}
.btn-ghost:hover { background: var(--teal-light); transform: translateY(-2px); }

/* Stats row */
.hero-stats {
  display: flex; gap: 2.5rem; margin-top: 3rem;
  padding-top: 2rem; border-top: 1px solid var(--border);
}
.stat-num {
  font-family: 'Manrope', sans-serif;
  font-size: 1.6rem; font-weight: 900;
  color: var(--teal-dark);
}
.stat-label {
  font-size: 0.6rem; text-transform: uppercase;
  letter-spacing: 0.14em; font-weight: 700;
  color: var(--muted); margin-top: 0.15rem;
}

/* Hero image panel */
.hero-visual {
  position: relative;
  display: flex; align-items: center; justify-content: center;
}
.hero-photo-wrap {
  width: 320px; height: 420px;
  border-radius: 40% 60% 55% 45% / 45% 50% 50% 55%;
  overflow: hidden;
  box-shadow: 0 30px 80px -10px rgba(13,63,82,0.22);
  animation: morphBlob 8s ease-in-out infinite;
  border: 4px solid var(--white);
}
@keyframes morphBlob {
  0%,100% { border-radius: 40% 60% 55% 45% / 45% 50% 50% 55%; }
  33%      { border-radius: 55% 45% 40% 60% / 55% 45% 55% 45%; }
  66%      { border-radius: 45% 55% 60% 40% / 50% 55% 45% 50%; }
}
.hero-photo-wrap img {
  width: 100%; height: 100%; object-fit: cover; object-position: top center;
  filter: saturate(0.92);
}
/* Floating chips */
.chip {
  position: absolute;
  background: var(--white);
  border-radius: 999px;
  padding: 0.55rem 1rem;
  font-size: 0.7rem; font-weight: 700;
  font-family: 'Manrope', sans-serif;
  letter-spacing: 0.06em;
  box-shadow: 0 8px 24px rgba(0,0,0,0.08);
  display: flex; align-items: center; gap: 0.4rem;
  white-space: nowrap;
}
.chip-tl { top: 10%; left: -18%; color: var(--teal-dark); }
.chip-br { bottom: 12%; right: -16%; color: var(--rose); }
.chip-icon { width: 20px; height: 20px; border-radius: 50%; display:flex; align-items:center; justify-content:center; }
.chip-tl .chip-icon { background: var(--teal-light); }
.chip-br .chip-icon { background: var(--rose-light); }

/* ─── Section scaffold ─── */
section { padding: 6rem 2rem; }
.section-inner { max-width: 1100px; margin: 0 auto; }
.section-label {
  display: inline-block;
  background: var(--section-bg); color: var(--teal);
  font-size: 0.65rem; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.18em;
  padding: 0.35rem 1rem; border-radius: 999px;
  margin-bottom: 0.9rem;
  font-family: 'Manrope', sans-serif;
}
.section-title {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(2rem, 3.5vw, 2.8rem);
  color: var(--teal-dark); letter-spacing: -0.02em;
  margin-bottom: 3.5rem;
}

/* ─── Experience ─── */
#experience { background: var(--white); }
.timeline { display: flex; flex-direction: column; gap: 0; }
.tl-item {
  display: grid; grid-template-columns: 220px 1fr;
  gap: 0 2.5rem; position: relative;
  padding-bottom: 2.8rem;
}
.tl-item::after {
  content: ''; position: absolute;
  left: 219px; top: 8px; bottom: 0;
  width: 1px; background: var(--border);
}
.tl-item:last-child::after { display: none; }
.tl-date-col { text-align: right; padding-top: 0.05rem; }
.tl-period {
  font-size: 0.72rem; font-weight: 700;
  color: var(--teal); text-transform: uppercase;
  letter-spacing: 0.08em; font-family: 'Manrope', sans-serif;
  line-height: 1.4;
}
.tl-company {
  font-size: 0.72rem; color: var(--muted);
  margin-top: 0.2rem; font-style: italic;
}
.tl-dot {
  position: absolute; left: 211px; top: 6px;
  width: 16px; height: 16px; border-radius: 50%;
  background: var(--teal); border: 3px solid var(--white);
  box-shadow: 0 0 0 2px var(--teal);
}
.tl-content { padding-left: 1.5rem; }
.tl-role {
  font-family: 'Manrope', sans-serif;
  font-size: 1.05rem; font-weight: 800;
  color: var(--ink); margin-bottom: 0.2rem;
}
.tl-type {
  display: inline-block;
  background: var(--teal-light); color: var(--teal);
  font-size: 0.6rem; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.1em;
  padding: 0.2rem 0.65rem; border-radius: 999px;
  margin-bottom: 0.85rem;
  font-family: 'Manrope', sans-serif;
}
.tl-bullets { list-style: none; display: flex; flex-direction: column; gap: 0.4rem; }
.tl-bullets li {
  font-size: 0.88rem; color: var(--muted);
  display: flex; gap: 0.6rem; align-items: flex-start;
  line-height: 1.55;
}
.tl-bullets li::before {
  content: '→'; color: var(--teal); font-size: 0.75rem;
  margin-top: 0.18rem; flex-shrink: 0;
}

/* ─── Education + Stay Abroad ─── */
#education { background: var(--sand); }
.edu-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 2rem; }
.edu-card {
  background: var(--white); border-radius: 1.25rem;
  padding: 2rem 2.2rem;
  border: 1px solid var(--border);
  transition: transform 0.25s cubic-bezier(.34,1.56,.64,1), box-shadow 0.25s;
}
.edu-card:hover { transform: translateY(-5px); box-shadow: 0 16px 40px -8px rgba(19,89,115,0.1); }
.edu-card-label {
  font-size: 0.6rem; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.15em;
  color: var(--rose); margin-bottom: 0.6rem;
  font-family: 'Manrope', sans-serif;
}
.edu-degree {
  font-family: 'Manrope', sans-serif;
  font-size: 1.05rem; font-weight: 800;
  color: var(--ink); margin-bottom: 0.3rem;
}
.edu-school { font-size: 0.82rem; color: var(--teal); font-weight: 500; margin-bottom: 0.9rem; }
.edu-meta { font-size: 0.78rem; color: var(--muted); }
.edu-meta span { font-weight: 600; color: var(--ink); }
.edu-period {
  font-size: 0.72rem; font-weight: 700;
  color: var(--muted); text-transform: uppercase;
  letter-spacing: 0.08em; font-family: 'Manrope', sans-serif;
  margin-bottom: 0.5rem; display: block;
}

/* ─── Skills & Languages ─── */
#skills { background: var(--teal-dark); }
#skills .section-label { background: rgba(255,255,255,0.12); color: #93cfec; }
#skills .section-title { color: #fff; }
.skills-layout { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 2.5rem; }
.skill-group-title {
  font-size: 0.65rem; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.18em;
  color: #93cfec; margin-bottom: 1.2rem;
  font-family: 'Manrope', sans-serif;
}
.skill-pill {
  display: inline-flex; align-items: center;
  background: rgba(255,255,255,0.1);
  color: #e8f4f8; border: 1px solid rgba(255,255,255,0.12);
  padding: 0.45rem 1rem; border-radius: 999px;
  font-size: 0.8rem; font-weight: 500;
  margin: 0.25rem 0.2rem 0 0;
  font-family: 'Manrope', sans-serif;
  transition: background 0.2s;
}
.skill-pill:hover { background: rgba(255,255,255,0.18); }
.lang-row {
  display: flex; justify-content: space-between; align-items: center;
  padding: 0.65rem 0; border-bottom: 1px solid rgba(255,255,255,0.08);
}
.lang-row:last-child { border-bottom: none; }
.lang-name { font-size: 0.9rem; color: #e8f4f8; font-weight: 500; }
.lang-level {
  font-size: 0.65rem; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.1em;
  color: #93cfec; background: rgba(255,255,255,0.08);
  padding: 0.25rem 0.7rem; border-radius: 999px;
  font-family: 'Manrope', sans-serif;
}

/* ─── About / Interests ─── */
#about { background: var(--white); }
.about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 3.5rem; align-items: start; }
.about-text p { font-size: 0.95rem; color: var(--muted); line-height: 1.8; margin-bottom: 1.1rem; }
.about-text p strong { color: var(--ink); font-weight: 600; }
.interest-list { display: flex; flex-wrap: wrap; gap: 0.75rem; margin-top: 0.5rem; }
.interest-tag {
  display: flex; align-items: center; gap: 0.5rem;
  background: var(--section-bg);
  color: var(--teal-dark);
  padding: 0.55rem 1rem; border-radius: 999px;
  font-size: 0.8rem; font-weight: 600;
  font-family: 'Manrope', sans-serif;
  transition: transform 0.2s, box-shadow 0.2s;
}
.interest-tag:hover { transform: translateY(-3px); box-shadow: 0 6px 16px rgba(19,89,115,0.1); }
.contact-card {
  background: var(--teal-dark); color: #fff;
  border-radius: 1.25rem; padding: 2.2rem 2.4rem;
}
.contact-card h3 {
  font-family: 'DM Serif Display', serif;
  font-size: 1.6rem; color: #fff; margin-bottom: 1.5rem;
}
.contact-row {
  display: flex; align-items: flex-start; gap: 1rem;
  margin-bottom: 1.2rem;
}
.contact-icon {
  width: 36px; height: 36px; border-radius: 50%;
  background: rgba(255,255,255,0.1);
  display: flex; align-items: center; justify-content: center;
  flex-shrink: 0;
}
.contact-icon .material-symbols-outlined { color: #93cfec; font-size: 1rem; }
.contact-info-label { font-size: 0.6rem; text-transform: uppercase; letter-spacing: 0.12em; opacity: 0.5; font-family: 'Manrope', sans-serif; }
.contact-info-val { font-size: 0.9rem; font-weight: 600; font-family: 'Manrope', sans-serif; }
.contact-info-val a { color: #fff; text-decoration: none; border-bottom: 1px solid transparent; transition: border-color 0.2s; }
.contact-info-val a:hover { border-color: rgba(255,255,255,0.5); }

/* ─── Footer ─── */
footer {
  background: var(--teal-deeper); color: rgba(255,255,255,0.5);
  padding: 2rem; text-align: center;
  font-size: 0.75rem; letter-spacing: 0.08em;
  text-transform: uppercase; font-family: 'Manrope', sans-serif;
}
footer span { color: #93cfec; }

/* ─── Page-load animations ─── */
.animate-in {
  opacity: 0; transform: translateY(28px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}
.animate-in.visible { opacity: 1; transform: translateY(0); }

/* ─── Responsive ─── */
@media (max-width: 900px) {
  .hero-inner { grid-template-columns: 1fr; gap: 3rem; }
  .hero-visual { display: none; }
  .tl-item { grid-template-columns: 1fr; }
  .tl-item::after, .tl-dot { display: none; }
  .tl-date-col { text-align: left; margin-bottom: 0.4rem; }
  .tl-content { padding-left: 0; }
  .edu-grid { grid-template-columns: 1fr; }
  .skills-layout { grid-template-columns: 1fr 1fr; }
  .about-grid { grid-template-columns: 1fr; }
}
@media (max-width: 600px) {
  .nav-links { display: none; }
  .skills-layout { grid-template-columns: 1fr; }
  section { padding: 4rem 1.2rem; }
  .hero { padding: 6rem 1.2rem 3rem; }
}
