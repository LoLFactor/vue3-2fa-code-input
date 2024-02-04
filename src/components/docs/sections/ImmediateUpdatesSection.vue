<script setup lang="ts">
import { ref } from 'vue';

import Section from '@/components/docs/Section.vue';
import Vue2FACodeInput from '@/components/Vue2FACodeInput.vue';

const fullCode = ref<string | null>(null);
const partialCode = ref<string | null>(null);
</script>

<template>
  <Section title="Immediate updates" anchor="immediate-updates">
    <div class="mb-8">
      <p class="mb-2">
        By default, the component doesn't update the <code>modelValue</code> until the code has been completely filled
        in.
        And when a character is deleted and the code becomes incomplete, it resets back to <code>null</code>. If you
        would like to change this behaviour, set <code>update-immediately</code> ont the component. This will make it so
        the provided reference is updated with each change.
        Keep in mind that when all characters are deleted, the reference will still be reset to <code>null</code>.
      </p>
      <p>You can see this difference in action by typing in the two inputs below.</p>
    </div>


    <div class="flex flex-col gap-4 md:flex-row md:gap-0 justify-around">
      <div class="flex flex-col items-center">
        <Vue2FACodeInput v-model="fullCode" :autofocus="false"/>

        <div class="mt-4">
          <p>Default behaviour: <strong>{{ fullCode ?? 'null' }}</strong></p>
        </div>
      </div>

      <div class="flex flex-col items-center">
        <Vue2FACodeInput v-model="partialCode" update-immediately :autofocus="false"/>

        <div class="mt-4">
          <p>Immediate updates: <strong>{{ partialCode ?? 'null' }}</strong></p>
        </div>
      </div>
    </div>
  </Section>
</template>
