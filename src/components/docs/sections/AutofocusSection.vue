<script setup lang="ts">
import { ref } from 'vue';

import Section from '@/components/docs/Section.vue';
import Vue2FACodeInput from '@/components/Vue2FACodeInput.vue';

const code = ref<string | null>(null);
</script>

<template>
  <Section title="Autofocus" anchor="autofocus">
    <p class="mb-8">
      The default behaviour is to autofocus the component, since the usual use-case is it sitting by itself, front
      and center on a page. If you need to turn off this behaviour, just set <code>:autofocus="false"</code> on
      the component.
    </p>

    <div class="flex flex-col items-center">
      <Vue2FACodeInput v-model="code"/>

      <div class="mt-4">
        <p>Inputted code: <strong>{{ code ?? 'null' }}</strong></p>
      </div>
    </div>
  </Section>
</template>
