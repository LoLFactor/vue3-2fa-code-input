<script setup lang="ts">
import { ref } from 'vue';

import Section from '@/components/docs/Section.vue';
import Vue2FACodeInput from '@/components/Vue2FACodeInput.vue';

const code = ref<string | null>(null);
</script>

<template>
  <Section title="Styling" anchor="styling">
    <div class="mb-8">
      <p class="mb-2">
        No default styles are included, but styling is pretty-straight-forward, since the component is a simple div that
        wraps an arbitrary number of inputs.
      </p>
      <p class="mb-2">
        There are 2 classes you have to provide styling for: <code>vue3-2fa-code-input</code> (which is the div
        container) and <code>vue3-2fa-code-input-box</code> (which are the individual character inputs). If you want,
        you can change these class names, the first by supplying <code>class</code> to the component itself, and for the
        input box there is a property named <code>inputClass</code>, so to change both class names you would do
        something like this: <code>
        &lt;Vue2FACodeInput class="you-container-class-here" input-class="your-input-box-class-here" v-model="yourRef"/>
      </code>.
      </p>
      <p class="mb-2">
        Keep in mind, the classes you supply get added to the existing ones and do not replace them, so those can still
        be used.
      </p>
      <p>
        For the sake of example, here's a version that adds more space in the middle, between the 3rd and 4th
        characters:
      </p>
    </div>

    <div class="flex flex-col items-center">
      <Vue2FACodeInput class="spaced-code-input" v-model="code" :autofocus="false"/>

      <div class="mt-4">
        <p>Inputted code: <strong>{{ code ?? 'null' }}</strong></p>
      </div>
    </div>

    <div class="mt-8">
      <p class="mb-2">
        And as a reference, here's the Tailwind code that styles all the inputs on this page and this particular one
        above:
      </p>

      <pre>
        <code class="block overflow-x-auto max-h-max leading-6">@layer components {
    .vue3-2fa-code-input {
        @apply flex gap-4;
    }

    .vue3-2fa-code-input-box {
        @apply block w-8 rounded-md border-[1px] bg-transparent border-gray-200 dark:border-gray-50 py-1.5 text-center text-gray-900 dark:text-white shadow-sm focus-visible:outline focus-visible:outline-indigo-500;
    }

    .spaced-code-input {
        & .vue3-2fa-code-input-box {
            &:nth-child(3) {
                @apply mr-4;
            }

            &:nth-child(4) {
                @apply ml-4;
            }
        }
    }
}</code>
        </pre>
    </div>
  </Section>
</template>
