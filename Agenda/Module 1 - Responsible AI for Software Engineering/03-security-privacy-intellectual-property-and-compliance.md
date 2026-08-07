# What Crosses the Boundary?

<div class="boundary-map">
  <div class="boundary-source"><tabler-device-laptop /><b>Your workspace</b></div>
  <div class="boundary-stream">
    <span v-click><tabler-message /> prompts</span>
    <span v-click><tabler-files /> files</span>
    <span v-click><tabler-terminal /> tool output</span>
    <span v-click><tabler-history /> history</span>
  </div>
  <div class="boundary-wall"><span>TRUST BOUNDARY</span></div>
  <div class="boundary-target"><tabler-cloud-lock /><b>AI service</b></div>
</div>

<div v-click class="caption">The visible prompt is only part of the payload.</div>

<!--
Repository-aware and agentic tools may collect broader context than the visible prompt. Provider terms, retention, telemetry, configured connectors, and enterprise controls matter.
-->

---

# Classify Before You Send

<div class="classification-stack">
  <div v-click class="class-public"><tabler-world /><b>PUBLIC</b><span>Approved tool</span></div>
  <div v-click class="class-internal"><tabler-building /><b>INTERNAL</b><span>Approved for internal data</span></div>
  <div v-click class="class-confidential"><tabler-lock /><b>CONFIDENTIAL</b><span>Explicit service + use case</span></div>
  <div v-click class="class-restricted"><tabler-shield-lock /><b>RESTRICTED</b><span>Policy + data owner approval</span></div>
</div>

<div v-click class="danger-strip"><tabler-key /> Secrets and credentials never become “just context.”</div>

<!--
Adapt these labels to the company's actual classification system. An enterprise subscription does not automatically authorize every data category.
-->

---

# Untrusted In. Untrusted Out.

<div class="attack-pipeline">
  <div v-click class="attack-input">
    <tabler-bug />
    <b>Malicious context</b>
    <span>issue · webpage · document · dependency</span>
  </div>
  <div v-click class="attack-model"><tabler-brain /> MODEL</div>
  <div v-click class="attack-output">
    <tabler-terminal-2 />
    <b>Unsafe output</b>
    <span>shell · SQL · HTML · infrastructure</span>
  </div>
</div>

<div v-click class="guardrail-row">
  <span><tabler-lock-access />least privilege</span>
  <span><tabler-box />sandbox</span>
  <span><tabler-list-check />validation</span>
  <span><tabler-user-check />approval</span>
</div>

<!--
Inputs may contain prompt injection or poisoned content. Outputs may contain insecure code, fabricated packages, or destructive commands. Module 7 explores these threats in depth.
-->

---

# Privacy: Shrink the Payload

<div class="privacy-transform">
  <div v-click="1" class="raw-record">
    <span>name: Ada Lovelace</span><span>email: ada@client.io</span><span>card: 4242…</span><span>error: parser:42</span>
  </div>
  <tabler-arrow-right v-click="2" class="transform-arrow" />
  <div v-click="2" class="clean-record">
    <span>user_id: synthetic-01</span><span>error: parser:42</span>
  </div>
</div>

<div class="privacy-steps">
  <span v-click="3">1 Necessity</span><span v-click="4">2 Minimize</span><span v-click="5">3 De-identify</span><span v-click="6">4 Authorize</span>
</div>

<!--
Synthetic or locally reproduced data is usually safer for debugging. De-identification is context-dependent and not always sufficient, especially for regulated processing.
-->

---

# IP Flows Both Ways

<div class="ip-flow">
  <div v-click>
    <tabler-login /><b>INPUT</b>
    <span>Right to share?</span><span>Trade secret?</span><span>Provider terms?</span>
  </div>
  <div class="ip-core"><tabler-scale />AI</div>
  <div v-click>
    <tabler-logout /><b>OUTPUT</b>
    <span>Original?</span><span>Compatible license?</span><span>Known provenance?</span>
  </div>
</div>

<div v-click class="signal-line">Generated ≠ safe to use, original, accurate, or protectable.</div>

<!--
Copyright and patent treatment varies by jurisdiction and continues to evolve. Escalate significant uncertainty to legal counsel rather than making a legal conclusion from the model's answer.
-->

---

# Compliance Follows Impact

<div class="risk-pyramid">
  <div v-click class="risk-minimal"><span>MINIMAL</span><b>Docs · formatting · public research</b></div>
  <div v-click class="risk-limited"><span>LIMITED</span><b>Transparency may be required</b></div>
  <div v-click class="risk-high"><span>HIGH</span><b>Employment · healthcare · safety · access</b></div>
  <div v-click class="risk-stop"><span>STOP</span><b>Prohibited use</b></div>
</div>

<div v-click class="caption">Do not self-classify a high-impact use case.</div>

<!--
Involve legal, privacy, security, and the business owner early. Existing privacy, employment, product safety, consumer, contract, and sector rules may apply alongside AI-specific regulation.
-->

---

# The 60-Second Preflight

<div class="preflight-ring">
  <div v-click><tabler-tool />Tool</div><div v-click><tabler-database />Data</div>
  <div v-click><tabler-file-description />Terms</div><div v-click><tabler-key />Access</div>
  <div v-click><tabler-bolt />Impact</div><div v-click><tabler-test-pipe />Evidence</div>
  <div v-click><tabler-lifebuoy />Escalation</div>
  <div class="preflight-core">GO<br><small>only if known</small></div>
</div>

<!--
Make this habitual before a prompt, agent session, connector installation, or AI-backed feature. If one answer is unknown, pause rather than guessing.
-->

---

# You Decide: Production Incident

<DecisionLab />

<!--
Ask the audience to vote before clicking. Prevention reduces likelihood; restricted access, safe environments, credential rotation, review, and normal change controls limit impact when prevention fails.
-->

---

# Security Is a Lifecycle

<div class="lifecycle-line">
  <div v-click><tabler-ruler /><b>Design</b><span>Threat model</span></div>
  <div v-click><tabler-code /><b>Develop</b><span>Supply chain</span></div>
  <div v-click><tabler-rocket /><b>Deploy</b><span>Isolation</span></div>
  <div v-click><tabler-heart-rate-monitor /><b>Operate</b><span>Monitor</span></div>
</div>

<div v-click class="takeaway"><tabler-shield-check-filled /> Secure by default, from context selection to incident response.</div>

<!--
References: NCSC Guidelines for Secure AI System Development, OWASP GenAI Security Project, EU AI Act overview, U.S. Copyright Office AI initiative, and NIST Privacy Framework.
-->
