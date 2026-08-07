# AI Strategy for Developers

<div class="hero-equation">
  <div v-motion :initial="{ opacity: 0, x: -40 }" :enter="{ opacity: 1, x: 0 }">
    <tabler-code class="hero-icon" />
    <span>More code</span>
  </div>
  <b v-click.fade>=</b>
  <div v-click.fade class="crossed"><tabler-x /> Strategy</div>
</div>

<div v-click class="hero-answer">
  <tabler-route /> Better outcomes, shorter feedback loops, controlled risk.
</div>

<!--
Open with the misconception: activity is not impact. AI strategy should improve lead time, quality, reliability, customer value, or developer experience, not merely increase generated code.
-->

---

# Start With the Constraint

<div class="funnel">
  <div v-click><tabler-hourglass /> <b>Bottleneck</b><span>What is slowing delivery?</span></div>
  <div v-click><tabler-sparkles /> <b>Intervention</b><span>Can AI change that constraint?</span></div>
  <div v-click><tabler-chart-dots /> <b>Evidence</b><span>Did the outcome improve?</span></div>
</div>

<div v-click class="signal-line">“Buy the best model” is procurement. “Cut onboarding time by 30%” is strategy.</div>

<!--
Ask the room for a current engineering bottleneck. Good examples include unfamiliar services, repetitive migrations, weak test coverage, or slow incident diagnosis.
-->

---

# Five Leverage Points

<div class="orbit">
  <div class="orbit-core"><tabler-brain /><span>Developer<br>judgment</span></div>
  <div v-click class="orbit-node n1"><tabler-search />Understand</div>
  <div v-click class="orbit-node n2"><tabler-bulb />Explore</div>
  <div v-click class="orbit-node n3"><tabler-hammer />Produce</div>
  <div v-click class="orbit-node n4"><tabler-shield-check />Verify</div>
  <div v-click class="orbit-node n5"><tabler-activity />Operate</div>
</div>

<div v-click class="caption">Best fit: clear context + fast feedback + verifiable result</div>

<!--
Producing code is only one leverage point. Understanding, exploration, and verification often create more value with lower risk. AI verification is an additional signal, not independent proof.
-->

---

# Earn Autonomy

<div class="autonomy-track">
  <div v-click><span>01</span><tabler-message-circle /><b>Assist</b><small>Explain</small></div>
  <div v-click><span>02</span><tabler-pencil /><b>Draft</b><small>Propose</small></div>
  <div v-click><span>03</span><tabler-terminal-2 /><b>Act</b><small>Modify</small></div>
  <div v-click><span>04</span><tabler-robot /><b>Automate</b><small>Run</small></div>
</div>

<div class="control-meter" v-click>
  <span>More autonomy</span><i></i><span>More evidence + control</span>
</div>

<!--
Teams earn autonomy through measurable reliability. High-impact tasks may intentionally remain advisory. Move right only when failures are detectable, actions reversible, permissions bounded, and an owner exists.
-->

---

# The Operating Loop

<div class="loop-diagram">
  <div v-click="1"><tabler-target />Choose</div>
  <div v-click="2"><tabler-lock />Constrain</div>
  <div v-click="3"><tabler-test-pipe />Verify</div>
  <div v-click="4"><tabler-chart-bar />Measure</div>
  <div v-click="5"><tabler-repeat />Standardize</div>
  <svg viewBox="0 0 400 240" aria-hidden="true"><path d="M200 30 C320 30 360 150 290 205 C210 265 70 210 55 120 C45 50 110 20 165 30" /></svg>
</div>

<div v-click="5" class="signal-line">Scale proven workflows, not isolated demos.</div>

<!--
Choose a valuable bounded use case. Constrain context, permissions, scope, and spend. Verify with evidence. Measure quality and rework. Standardize only what proves useful.
-->

---

# Strategy Gate

<div class="gate-grid">
  <div v-click><tabler-target-arrow /><b>Outcome</b><span>What improves?</span></div>
  <div v-click><tabler-database /><b>Data</b><span>What crosses the boundary?</span></div>
  <div v-click><tabler-checkbox /><b>Proof</b><span>How is it verified?</span></div>
  <div v-click><tabler-alert-triangle /><b>Failure</b><span>How is impact contained?</span></div>
  <div v-click><tabler-user-check /><b>Owner</b><span>Who signs off?</span></div>
  <div v-click><tabler-arrows-diagonal /><b>Scale</b><span>Expand or stop?</span></div>
</div>

<!--
Use this as the reusable strategy checkpoint. AI strategy is a portfolio of measured and governed workflows, not a blanket adoption mandate.
-->

---

# Strategy in One Frame

<div class="photo-frame strategy-photo">
  <div class="photo-overlay">
    <span>INPUT</span><b>A real engineering constraint</b>
    <tabler-arrow-down />
    <span>OUTPUT</span><b>A measured, governed workflow</b>
  </div>
</div>

<div v-click class="takeaway"><tabler-circle-check-filled /> Improve the system of work, not the volume of output.</div>

<!--
Close the section and transition to the company policy, which defines the local boundaries for these workflows.
References: NIST AI RMF and NIST AI RMF Playbook.
-->
