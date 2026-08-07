# Start With the Task

<div class="tool-lens">
  <div v-click><tabler-database /><b>Sensitivity</b></div>
  <div v-click><tabler-folders /><b>Context</b></div>
  <div v-click><tabler-player-play /><b>Action</b></div>
  <div v-click><tabler-checkbox /><b>Verifiability</b></div>
  <div v-click><tabler-bolt /><b>Impact</b></div>
  <div class="tool-lens-core"><tabler-tool />FIT</div>
</div>

<div v-click class="signal-line">Capability without appropriate control is not a fit.</div>

<!--
Do not begin with model rankings or vendor popularity. Tool choice is a workflow and risk decision as much as a capability decision.
-->

---

# The Tool Is More Than the Model

<div class="stack-diagram">
  <div v-click class="stack-user"><tabler-user />Human intent</div>
  <div v-click class="stack-harness"><tabler-adjustments-horizontal />Harness: context · permissions · tools · evidence</div>
  <div v-click class="stack-model"><tabler-brain />Model: reasoning · generation</div>
  <div v-click class="stack-world"><tabler-server />Files · terminal · network · production</div>
</div>

<div v-click class="caption">The same model can be low-risk chat or a high-impact agent.</div>

<!--
The harness determines what context the model receives and what actions it can take. This distinction prepares participants for Module 3.
-->

---

# A Portfolio of Tools

<div class="tool-gallery">
  <div v-click><tabler-message-chatbot /><b>CHAT</b><span>Explain · brainstorm</span></div>
  <div v-click><tabler-code-dots /><b>IDE</b><span>Complete · edit</span></div>
  <div v-click><tabler-topology-star-3 /><b>REPO</b><span>Search · plan</span></div>
  <div v-click><tabler-robot /><b>AGENT</b><span>Execute · verify</span></div>
  <div v-click><tabler-shield-search /><b>SPECIALIST</b><span>Test · secure</span></div>
  <div v-click><tabler-device-desktop /><b>LOCAL</b><span>Constrain data</span></div>
</div>

<!--
Each category has a different context and action profile. Specialized deterministic tools may provide stronger evidence than a general model for testing and security.
-->

---

# Match Autonomy to Consequence

<div class="risk-matrix">
  <div class="axis-y">CONSEQUENCE ↑</div><div class="axis-x">AUTONOMY →</div>
  <div v-click class="dot d1"><span>Public API<br>explanation</span></div>
  <div v-click class="dot d2"><span>Draft unit<br>tests</span></div>
  <div v-click class="dot d3"><span>Repository<br>refactor</span></div>
  <div v-click class="dot d4"><span>Sensitive log<br>analysis</span></div>
  <div v-click class="dot d5"><span>Production<br>change</span></div>
  <div class="matrix-zone zone-safe">NORMAL REVIEW</div>
  <div class="matrix-zone zone-control">CONSTRAIN + APPROVE</div>
</div>

<!--
A production agent should usually propose while a human approves execution. People-impacting decisions require an approved governed system, not an improvised prompt.
-->

---

# The Selection Gate

<div class="selection-gate">
  <div class="gate-input">Candidate tool</div>
  <div class="gate-filters">
    <span v-click><tabler-rosette-discount-check />Approved?</span>
    <span v-click><tabler-database-cog />Data controls?</span>
    <span v-click><tabler-lock-access />Access controls?</span>
    <span v-click><tabler-sparkles />Capable?</span>
    <span v-click><tabler-receipt />Evidence?</span>
    <span v-click><tabler-coin />Worth it?</span>
  </div>
  <div v-click class="gate-output"><tabler-circle-check />Use</div>
</div>

<div v-click class="danger-strip"><tabler-ban /> One failed mandatory control = reject.</div>

<!--
Total cost includes integration, review, correction, latency, and incidents, not just token price. Approval and controls precede capability.
-->

---

# Route, Don't Overbuy

<div class="router">
  <div class="router-input"><tabler-git-branch />TASK</div>
  <div v-click class="route r-fast"><b>FAST</b><span>Routine + cheap</span></div>
  <div v-click class="route r-deep"><b>DEEP</b><span>Complex reasoning</span></div>
  <div v-click class="route r-protected"><b>PROTECTED</b><span>Sensitive context</span></div>
  <div v-click class="route r-special"><b>SPECIALIST</b><span>Deterministic proof</span></div>
</div>

<div v-click class="caption">Escalate capability and cost only when the task requires it.</div>

<!--
Model selection and cost optimization appear in Module 2. The key concept here is task and risk routing.
-->

---

# Design Your Route

<div class="worksheet">
  <div v-click><span>01</span><b>DATA</b><small>classification?</small></div>
  <div v-click><span>02</span><b>CONTEXT</b><small>what is needed?</small></div>
  <div v-click><span>03</span><b>ACTION</b><small>maximum authority?</small></div>
  <div v-click><span>04</span><b>PROOF</b><small>how detected?</small></div>
  <div v-click><span>05</span><b>TOOL</b><small>approved category?</small></div>
  <div v-click><span>06</span><b>HUMAN</b><small>approval point?</small></div>
</div>

<div v-click class="takeaway"><tabler-route /> If you cannot verify the result, reduce scope or keep AI advisory.</div>

<!--
Give participants one minute to map a weekly task. Invite one low-risk and one high-impact example.
-->
