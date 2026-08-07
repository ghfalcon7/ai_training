# Work Can Move. Accountability Cannot.

<div class="accountability-scene">
  <div v-motion :initial="{ x: -60, opacity: 0 }" :enter="{ x: 0, opacity: 1 }"><tabler-robot /><span>performs</span></div>
  <div class="handoff-arrow"><tabler-arrow-right /></div>
  <div v-click><tabler-user-shield /><span>owns</span></div>
</div>

<div v-click class="ownership-list">
  <span>appropriateness</span><span>authorized access</span><span>verification</span><span>approval</span><span>monitoring</span>
</div>

<!--
“The AI produced it” is not an approval or transfer of responsibility. Accountability means someone has authority, competence, and responsibility for the outcome.
-->

---

# Is the Human Loop Real?

<div class="oversight-console">
  <div v-click><tabler-map /><b>Context</b><span>Understand the goal</span></div>
  <div v-click><tabler-school /><b>Competence</b><span>Evaluate the output</span></div>
  <div v-click><tabler-clock /><b>Time</b><span>Review, not rubber-stamp</span></div>
  <div v-click><tabler-gavel /><b>Authority</b><span>Reject or rollback</span></div>
  <div v-click><tabler-microscope /><b>Evidence</b><span>Sources, diffs, tests</span></div>
</div>

<div v-click class="danger-strip"><tabler-eye-off /> A tired reviewer is not a control.</div>

<!--
Human-in-the-loop is not automatically safe. Automation bias and review overload turn approval into theater. Keep changes reviewable and provide executable evidence.
-->

---

# Governance Is a Dimmer, Not a Switch

<div class="governance-dial">
  <div v-click class="dial-segment s-low"><b>LOW</b><span>normal review</span></div>
  <div v-click class="dial-segment s-mid"><b>MODERATE</b><span>tests + traceability</span></div>
  <div v-click class="dial-segment s-high"><b>HIGH</b><span>risk review + monitoring</span></div>
  <div v-click class="dial-segment s-stop"><b>PROHIBITED</b><span>stop + escalate</span></div>
</div>

<div v-click class="caption">Increase governance with sensitivity, consequence, irreversibility, and low detectability.</div>

<!--
Governance should be proportionate. Do not force low-risk interactions through a committee, and do not let high-risk exceptions be approved by an individual developer.
-->

---

# Accountability Map

<div class="responsibility-map">
  <div v-click><tabler-code /><b>Developer</b><span>use + validate</span></div>
  <div v-click><tabler-eye-check /><b>Reviewer</b><span>independent approval</span></div>
  <div v-click><tabler-crown /><b>Owner</b><span>intent + impact</span></div>
  <div v-click><tabler-shield-cog /><b>Specialists</b><span>controls + advice</span></div>
  <div v-click><tabler-building-bank /><b>Risk owner</b><span>appetite + exception</span></div>
  <svg viewBox="0 0 600 200"><path d="M60 100 H540" /></svg>
</div>

<div v-click class="signal-line">Every production AI workflow needs a named owner.</div>

<!--
One person may hold multiple roles in a small team, but responsibilities remain explicit. Name the intended use, prohibited use, controls, approval points, monitoring, and incident path.
-->

---

# Claims Become Trust Through Evidence

<div class="evidence-chain">
  <div v-click><tabler-message-chatbot /><b>CLAIM</b><span>“This change is safe.”</span></div>
  <tabler-arrow-right v-click />
  <div v-click><tabler-git-compare /><b>DIFF</b><span>What changed?</span></div>
  <tabler-arrow-right v-click />
  <div v-click><tabler-test-pipe /><b>TEST</b><span>What passed?</span></div>
  <tabler-arrow-right v-click />
  <div v-click><tabler-user-check /><b>DECISION</b><span>Who approved?</span></div>
</div>

<div v-click class="caption">Generated explanations are claims. Observations are evidence.</div>

<!--
Record evidence proportional to risk: scope, tool/version, data sources, permissions, artifact, tests, scans, approvals, deployment, and incidents. Do not indiscriminately log sensitive prompts.
-->

---

# Incident Response Is Still Incident Response

<div class="incident-timeline">
  <div v-click><span>00:00</span><tabler-player-stop /><b>Contain</b></div>
  <div v-click><span>00:05</span><tabler-shield-lock /><b>Protect</b></div>
  <div v-click><span>00:15</span><tabler-bell-ringing /><b>Report</b></div>
  <div v-click><span>00:30</span><tabler-file-search /><b>Preserve</b></div>
  <div v-click><span>NEXT</span><tabler-tool /><b>Correct</b></div>
  <div v-click><span>LEARN</span><tabler-refresh /><b>Improve</b></div>
</div>

<div v-click class="signal-line">Report near misses before they become incidents.</div>

<!--
Integrate AI failures with existing incident processes. Examine context, permissions, validation, interfaces, and incentives rather than blaming the model alone.
-->

---

# The Responsible Developer Contract

<div class="contract">
  <div v-click><tabler-rosette-discount-check />Approved purpose</div>
  <div v-click><tabler-filter />Minimum context</div>
  <div v-click><tabler-lock-access />Bounded autonomy</div>
  <div v-click><tabler-shield-question />Untrusted by default</div>
  <div v-click><tabler-test-pipe />Evidence by impact</div>
  <div v-click><tabler-user-check />Human accountability</div>
</div>

<div v-click class="contract-signature">
  <span>ENGINEER</span><i></i><b>Use AI boldly inside clear boundaries.</b>
</div>

<!--
Ask which commitment is easiest to forget under deadline pressure. This contract can become a team checklist or pull-request template.
References: NIST AI RMF, NIST Generative AI Profile, EU AI Act overview, and NCSC secure AI guidelines.
-->
