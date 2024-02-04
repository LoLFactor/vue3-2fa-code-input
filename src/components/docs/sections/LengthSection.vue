<script setup lang="ts">
import { ref } from 'vue';

import Section from '@/components/docs/Section.vue';
import Vue2FACodeInput from '@/components/Vue2FACodeInput.vue';

const shortCode = ref<string | null>(null);
const longCode = ref<string | null>(null);
</script>

<template>
  <Section title="Length" anchor="length">
    <p class="mb-8">
      The default length of the input is set to <code>6</code> characters, this being the most common, but you can
      change it by setting the <code>length</code> parameter on the component. In this example, the long code has
      <code>:length="9"</code>.
    </p>

    <div class="flex flex-col gap-4 md:flex-row md:gap-0 justify-around">
      <div class="flex flex-col items-center">
        <Vue2FACodeInput v-model="shortCode" :autofocus="false"/>

        <div class="mt-4">
          <p>Short code: <strong>{{ shortCode ?? 'null' }}</strong></p>
        </div>
      </div>

      <div class="flex flex-col items-center">
        <Vue2FACodeInput v-model="longCode" :length="9" :autofocus="false"/>

        <div class="mt-4">
          <p>Long code: <strong>{{ longCode ?? 'null' }}</strong></p>
        </div>
      </div>
    </div>
  </Section>
</template>
