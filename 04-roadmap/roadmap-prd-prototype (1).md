# Roadmap, PRD & Prototype (Module 4)

## Your strategic anchors
- **Persona (M2), who are you solving for?:** A long-time streaming subscriber who wants to discover great new content but feels overwhelmed by the size of the catalog.
- **Primary success metric (M3), your leading indicator:** Decrease in percentage of Wanderers
- **Moment of misery (M2), the specific friction blocking the goal:** Users leave the app because content curation is poor
- **Guardrail metric (M3), what must not drop or break:** The level of Casual Browsers and Power Users

## Scan the backlog & set a human baseline
- **My instinctive “quick wins” before touching the AI (2 to 3 feature IDs + why):** A4 Mood-based entry point: minimal input from user allows easy recommendations
A5 Personalized Spotlight Queue: AI recommendations are low cost but could provide a high level of personalization

## Audit, override & decide
- **Where did you override the AI? (feature + old vs. new score + why):** _(not filled in)_
- **Did the AI over-value a Sales/Eng request your M2 interviews don’t support?:** _(not filled in)_
- **Did it underweight something your M3 cohort/funnel data strongly supports?:** _(not filled in)_

## Generate your interactive roadmap
- **My “Now” lane (this sprint), the 2 to 3 quick wins I’ll build first:** - A4 Mood-Based Entry Point, 
- A9 Advanced Filter Engine,
- **What I cut, and the “no” I’m protecting the scope from:** - A6 Spotlight Digest Email, 
- A8 Watch Party (Spotlight),
- **Prototype/roadmap screenshot link (paste into your deliverables):** --quick-win: #27c281;
  --major-project: #7c8cff;
  --fill-in: #f2b94b;
  --time-sinker: #ef6b73;

  --now: #8ea0ff;
  --next: #63d1aa;
  --later: #c7a0ff;
  --cut: #ef6b73;

  --shadow: 0 18px 50px rgba(0,0,0,0.22);
}

* {
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  background:
    radial-gradient(circle at top left, rgba(124,140,255,0.14), transparent 32rem),
    radial-gradient(circle at top right, rgba(99,209,170,0.08), transparent 28rem),
    var(--bg);
  color: var(--text);
  min-height: 100vh;
}

button,
select {
  font: inherit;
}

.shell {
  width: min(1400px, calc(100% - 32px));
  margin: 0 auto;
  padding: 32px 0 56px;
}

.hero {
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 24px;
  align-items: end;
  margin-bottom: 28px;
}

.eyebrow {
  color: var(--accent);
  font-size: 0.78rem;
  font-weight: 800;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  margin-bottom: 10px;
}

h1 {
  margin: 0;
  font-size: clamp(2rem, 5vw, 4.8rem);
  line-height: 0.96;
  letter-spacing: -0.055em;
  max-width: 900px;
}

.hero-copy {
  color: var(--muted);
  font-size: 1rem;
  margin: 18px 0 0;
  max-width: 760px;
  line-height: 1.65;
}

.team-chip {
  justify-self: end;
  padding: 12px 16px;
  border: 1px solid var(--line);
  border-radius: 999px;
  color: var(--muted);
  background: rgba(255,255,255,0.045);
  white-space: nowrap;
  box-shadow: var(--shadow);
}

.toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  justify-content: space-between;
  align-items: center;
  margin: 24px 0;
  padding: 12px;
  border: 1px solid var(--line);
  background: rgba(18,25,50,0.84);
  backdrop-filter: blur(18px);
  border-radius: 18px;
  position: sticky;
  top: 12px;
  z-index: 20;
  box-shadow: var(--shadow);
}

.filters,
.actions {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.filter-btn,
.action-btn {
  appearance: none;
  border: 1px solid var(--line);
  background: rgba(255,255,255,0.04);
  color: var(--muted);
  border-radius: 12px;
  padding: 9px 12px;
  cursor: pointer;
  transition: 160ms ease;
}

.filter-btn:hover,
.action-btn:hover,
.filter-btn.active {
  color: var(--text);
  background: rgba(124,140,255,0.14);
  border-color: rgba(124,140,255,0.5);
  transform: translateY(-1px);
}

.roadmap {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 18px;
}

.lane {
  min-width: 0;
  background: rgba(18,25,50,0.72);
  border: 1px solid var(--line);
  border-radius: 22px;
  overflow: hidden;
  box-shadow: var(--shadow);
}

.lane-header {
  padding: 18px 18px 14px;
  border-bottom: 1px solid var(--line);
}

.lane-title-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 16px;
}

.lane h2 {
  margin: 0;
  font-size: 1.05rem;
  letter-spacing: 0.08em;
}

.lane-count {
  font-size: 0.78rem;
  color: var(--muted);
  border: 1px solid var(--line);
  border-radius: 999px;
  padding: 5px 9px;
}

.lane-subtitle {
  margin: 7px 0 0;
  color: var(--muted);
  font-size: 0.85rem;
}

.lane[data-lane="NOW"] h2 { color: var(--now); }
.lane[data-lane="NEXT"] h2 { color: var(--next); }
.lane[data-lane="LATER"] h2 { color: var(--later); }

.cards {
  padding: 14px;
  display: grid;
  gap: 12px;
  min-height: 180px;
}

.card {
  background: linear-gradient(180deg, rgba(255,255,255,0.055), rgba(255,255,255,0.025));
  border: 1px solid var(--line);
  border-radius: 16px;
  padding: 16px;
  transition: 180ms ease;
  cursor: pointer;
  outline: none;
}

.card:hover,
.card:focus-visible,
.card.expanded {
  border-color: rgba(124,140,255,0.52);
  transform: translateY(-2px);
  box-shadow: 0 14px 30px rgba(0,0,0,0.22);
}

.card-top {
  display: flex;
  justify-content: space-between;
  gap: 12px;
  align-items: flex-start;
}

.feature-id {
  color: var(--muted);
  font-size: 0.75rem;
  font-weight: 800;
  letter-spacing: 0.1em;
  margin-bottom: 6px;
}

.feature-name {
  margin: 0;
  font-size: 1rem;
  line-height: 1.35;
}

.badge {
  flex: 0 0 auto;
  font-size: 0.7rem;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  padding: 6px 8px;
  border-radius: 999px;
  color: #07111b;
}

.quick-win { background: var(--quick-win); }
.major-project { background: var(--major-project); }
.fill-in { background: var(--fill-in); }
.time-sinker { background: var(--time-sinker); }

.rationale {
  margin: 13px 0 0;
  color: #d5daf0;
  font-size: 0.9rem;
  line-height: 1.55;
}

.details {
  display: grid;
  grid-template-rows: 0fr;
  transition: grid-template-rows 180ms ease, margin-top 180ms ease;
  margin-top: 0;
}

.details > div {
  overflow: hidden;
}

.card.expanded .details {
  grid-template-rows: 1fr;
  margin-top: 14px;
}

.score-row {
  display: grid;
  grid-template-columns: repeat(2, minmax(0,1fr));
  gap: 8px;
}

.score {
  border: 1px solid var(--line);
  border-radius: 10px;
  padding: 9px 10px;
  color: var(--muted);
  background: rgba(0,0,0,0.14);
  font-size: 0.8rem;
}

.score strong {
  display: block;
  color: var(--text);
  font-size: 0.98rem;
  margin-top: 2px;
}

.cut-section {
  margin-top: 22px;
  border: 1px solid rgba(239,107,115,0.28);
  background: rgba(239,107,115,0.06);
  border-radius: 22px;
  overflow: hidden;
  box-shadow: var(--shadow);
}

.cut-header {
  padding: 18px;
  border-bottom: 1px solid rgba(239,107,115,0.2);
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
}

.cut-header h2 {
  margin: 0;
  color: var(--cut);
  font-size: 1.05rem;
  letter-spacing: 0.08em;
}

.cut-header p {
  margin: 5px 0 0;
  color: var(--muted);
  font-size: 0.85rem;
}

.cut-grid {
  padding: 14px;
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 12px;
}

.cut-card {
  border-color: rgba(239,107,115,0.22);
}

.hidden {
  display: none !important;
}

.legend {
  margin-top: 22px;
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  color: var(--muted);
  font-size: 0.78rem;
}

.legend-item {
  display: flex;
  align-items: center;
  gap: 7px;
}

.dot {
  width: 9px;
  height: 9px;
  border-radius: 50%;
}

.empty {
  color: var(--muted);
  border: 1px dashed var(--line);
  border-radius: 14px;
  padding: 20px;
  text-align: center;
  font-size: 0.85rem;
}

@media (max-width: 980px) {
  .roadmap {
    grid-template-columns: 1fr;
  }

  .hero {
    grid-template-columns: 1fr;
  }

  .team-chip {
    justify-self: start;
  }
}

@media (max-width: 640px) {
  .shell {
    width: min(100% - 20px, 1400px);
    padding-top: 20px;
  }

  .cut-grid {
    grid-template-columns: 1fr;
  }

  .toolbar {
    top: 6px;
  }

  .card-top {
    flex-direction: column;
  }
}
