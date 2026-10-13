* { box-sizing: border-box; }

:root {
  --navy: #172033;
  --blue: #3d6df2;
  --blue-soft: #edf2ff;
  --text: #293244;
  --muted: #778195;
  --line: #e6e9ef;
  --bg: #f7f8fb;
  --white: #ffffff;
  --green: #2f9b71;
  --orange: #d98a38;
  --red: #d65c61;
}

html { scroll-behavior: smooth; }

body {
  margin: 0;
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  color: var(--text);
  background: var(--bg);
}

.navbar {
  height: 78px;
  padding: 0 7%;
  background: var(--white);
  border-bottom: 1px solid var(--line);
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.brand { display: flex; align-items: center; gap: 12px; }
.brand-mark {
  width: 42px; height: 42px; border-radius: 12px;
  background: var(--navy); color: white;
  display: grid; place-items: center;
  font-weight: 800; letter-spacing: -1px;
}
.brand h1 { margin: 0; font-size: 15px; color: var(--navy); }
.brand span { font-size: 11px; color: var(--muted); }
.nav-link { color: var(--text); text-decoration: none; font-size: 13px; font-weight: 600; }

main { max-width: 1180px; margin: auto; padding: 55px 24px 30px; }

.hero {
  display: grid;
  grid-template-columns: 1.35fr .65fr;
  gap: 35px;
  align-items: center;
  margin-bottom: 42px;
}
.eyebrow {
  margin: 0 0 10px;
  font-size: 10px;
  font-weight: 800;
  letter-spacing: 1.8px;
  color: var(--blue);
}
.hero h2 { margin: 0; font-size: clamp(34px, 5vw, 56px); line-height: 1.03; letter-spacing: -2.5px; color: var(--navy); }
.hero h2 span { color: var(--blue); }
.hero-text { max-width: 620px; color: var(--muted); line-height: 1.7; margin: 22px 0; }
.hero-tags { display: flex; gap: 8px; flex-wrap: wrap; }
.hero-tags span {
  background: var(--blue-soft); color: var(--blue);
  border-radius: 999px; padding: 8px 12px; font-size: 11px; font-weight: 700;
}

.hero-stat {
  background: var(--navy); min-height: 250px; border-radius: 22px;
  display: grid; place-items: center; padding: 25px;
  box-shadow: 0 18px 45px rgba(23,32,51,.13);
}
.mini-tree { width: 100%; text-align: center; color: white; }
.tree-node, .tree-result {
  display: inline-block; padding: 12px 17px; border-radius: 10px;
  font-size: 12px; font-weight: 700;
}
.tree-node { background: #2c3a57; border: 1px solid #43506b; }
.tree-result { margin-top: 15px; background: var(--blue); }
.branches { display: flex; justify-content: space-around; gap: 8px; margin: 12px 0 0; }
.branch { display: flex; flex-direction: column; align-items: center; gap: 7px; font-size: 10px; color: #b8c2d6; }
.branch i { width: 1px; height: 24px; background: #59657e; display: block; }

.workspace { display: grid; grid-template-columns: 1.55fr .85fr; gap: 20px; align-items: stretch; }
.form-card, .result-card, .about {
  background: var(--white); border: 1px solid var(--line); border-radius: 20px;
}
.form-card { padding: 30px; }
.section-heading { display: flex; align-items: flex-start; justify-content: space-between; margin-bottom: 24px; }
.section-heading h3, .about h3 { margin: 0; color: var(--navy); font-size: 23px; }
.required { font-size: 10px; color: var(--muted); background: var(--bg); padding: 7px 10px; border-radius: 8px; }

.grid { display: grid; grid-template-columns: 1fr 1fr; gap: 18px; }
label { font-size: 12px; font-weight: 700; color: var(--text); }
label.full { grid-column: 1 / -1; }
input {
  width: 100%; margin-top: 8px; border: 1px solid var(--line); background: #fbfcfe;
  padding: 13px 14px; border-radius: 10px; outline: none; color: var(--text);
  font-size: 13px; transition: .2s;
}
input:focus { border-color: var(--blue); background: white; box-shadow: 0 0 0 3px var(--blue-soft); }

button {
  margin-top: 24px; width: 100%; border: 0; border-radius: 11px;
  background: var(--navy); color: white; padding: 15px 18px;
  display: flex; align-items: center; justify-content: center; gap: 12px;
  font-weight: 800; cursor: pointer; transition: .2s;
}
button:hover { background: #263451; transform: translateY(-1px); }
button:disabled { opacity: .65; cursor: wait; }
.arrow { font-size: 18px; }

.result-card { padding: 30px; min-height: 100%; position: relative; overflow: hidden; }
.result-card:before {
  content: ""; position: absolute; width: 170px; height: 170px; border-radius: 50%;
  background: var(--blue-soft); right: -70px; top: -70px; z-index: 0;
}
.result-top { display: flex; justify-content: space-between; position: relative; z-index: 1; }
.status-dot { width: 8px; height: 8px; background: #b8c1d2; border-radius: 50%; margin-top: 3px; }
#emptyState { text-align: center; padding: 50px 15px 35px; position: relative; }
.result-icon { font-size: 42px; color: #b6bfd0; }
#emptyState h3 { margin: 12px 0 7px; color: var(--navy); }
#emptyState p { margin: 0; font-size: 12px; line-height: 1.7; color: var(--muted); }

.hidden { display: none !important; }
.result-label { color: var(--muted); font-size: 12px; margin: 45px 0 5px; }
.prediction-label { font-size: 42px; font-weight: 900; letter-spacing: -1px; color: var(--blue); }
.prediction-text { color: var(--muted); font-size: 12px; line-height: 1.6; }
.confidence-box { margin-top: 25px; }
.confidence-row { display: flex; justify-content: space-between; font-size: 11px; color: var(--muted); }
.confidence-row strong { color: var(--navy); }
.progress { height: 7px; background: #edf0f5; border-radius: 999px; margin-top: 9px; overflow: hidden; }
.progress span { display: block; height: 100%; width: 0; background: var(--blue); border-radius: inherit; transition: width .5s; }
.model-note { border-top: 1px solid var(--line); padding: 12px 0 0; margin-top: 18px; display: flex; justify-content: space-between; font-size: 10px; color: var(--muted); }
.model-note strong { color: var(--text); }

.about { margin-top: 20px; padding: 27px 30px; }
.pipeline { display: grid; grid-template-columns: repeat(5, 1fr); margin-top: 22px; gap: 10px; }
.pipeline div { background: var(--bg); border-radius: 12px; padding: 16px; }
.pipeline b { display: block; color: var(--blue); font-size: 10px; margin-bottom: 8px; }
.pipeline span { font-size: 11px; font-weight: 700; color: var(--text); }

footer {
  max-width: 1180px; margin: 25px auto 0; padding: 25px 24px 35px;
  color: var(--muted); font-size: 10px; display: flex; justify-content: space-between;
}

@media (max-width: 850px) {
  .hero, .workspace { grid-template-columns: 1fr; }
  .pipeline { grid-template-columns: 1fr 1fr; }
}
@media (max-width: 550px) {
  .navbar { padding: 0 20px; }
  .nav-link { display: none; }
  main { padding: 35px 15px 20px; }
  .grid { grid-template-columns: 1fr; }
  label.full { grid-column: auto; }
  .pipeline { grid-template-columns: 1fr; }
  footer { padding-left: 15px; padding-right: 15px; }
}
