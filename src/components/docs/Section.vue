<script setup lang="ts">
const props = defineProps<{ title: string, anchor: string }>();
</script>

<template>
  <div>
    <h1 class="mb-8 text-3xl font-bold leading-tight tracking-tight text-gray-900 dark:text-white" :id="props.anchor">
      {{ props.title }}
    </h1>
    <slot/>
  </div>
</template>
