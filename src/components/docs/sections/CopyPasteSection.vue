<script setup lang="ts">
import { ref } from 'vue';

import Section from '@/components/docs/Section.vue';
import Vue2FACodeInput from '@/components/Vue2FACodeInput.vue';

const code = ref<string | null>(null);
</script>

<template>
  <Section title="Copy-Paste" anchor="copy-paste">
    <p class="mb-8">
      The input supports copy-pasting, but will only accept pasted content that matches its length. Any pasted content
      that does not match the length will just be ignored.
    </p>

    <div class="flex flex-col items-center">
      <div class="mb-8">
        <p class="mb-2">These will work: <code>123456</code>, <code>ABCDEF</code></p>
        <p>These will NOT: <code>12345</code>, <code>ABCDEFG</code></p>
      </div>

      <Vue2FACodeInput v-model="code"/>

      <div class="mt-4">
        <p>Pasted code: <strong>{{ code ?? 'null' }}</strong></p>
      </div>
    </div>
  </Section>
</template>
