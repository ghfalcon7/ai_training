<script setup lang="ts">
import { computed, ref } from 'vue'

const choice = ref<'paste' | 'sanitize' | 'local' | null>(null)

const outcomes = {
  paste: {
    verdict: 'Stop',
    detail: 'Customer data and a live credential cross an unapproved boundary.',
    className: 'danger',
  },
  sanitize: {
    verdict: 'Proceed with controls',
    detail: 'Remove identifiers and secrets, minimize the sample, then use an approved account.',
    className: 'warning',
  },
  local: {
    verdict: 'Preferred',
    detail: 'Reproduce with synthetic data and keep sensitive production context out of the prompt.',
    className: 'safe',
  },
}

const outcome = computed(() => choice.value ? outcomes[choice.value] : null)
</script>

<template>
  <div class="decision-lab">
    <div class="decision-context">
      <div class="terminal-bar"><span /><span /><span /></div>
      <code>500 POST /checkout</code>
      <p>Log contains a customer record<br>and an Authorization header.</p>
    </div>

    <div class="decision-actions">
      <button :class="{ active: choice === 'paste' }" @click="choice = 'paste'">
        <tabler-copy /> Paste the full log
      </button>
      <button :class="{ active: choice === 'sanitize' }" @click="choice = 'sanitize'">
        <tabler-filter /> Sanitize first
      </button>
      <button :class="{ active: choice === 'local' }" @click="choice = 'local'">
        <tabler-flask /> Reproduce locally
      </button>
    </div>

    <div class="decision-result" :class="outcome?.className">
      <template v-if="outcome">
        <strong>{{ outcome.verdict }}</strong>
        <span>{{ outcome.detail }}</span>
      </template>
      <template v-else>
        <strong>Choose a response</strong>
        <span>The safest useful path is not always “do nothing.”</span>
      </template>
    </div>
  </div>
</template>
