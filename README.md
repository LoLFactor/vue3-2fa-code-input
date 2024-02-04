# Vue 3 2FA Code Input

Vue 3 input component for 2FA codes. Is alpha-numerically agnostic, supports copy-pasting and is written in Typescript.

See it in action in the [interactive documentation](https://lolfactor.github.io/vue3-2fa-code-input/).

## Getting started

First, install the package using your favorite package manager:

```
<your-favorite-package-manager> install @loltech/vue-2fa-code-input
```

then import the component and use it:

```vue

<script setup lang="ts">
  import { ref } from 'vue';
  import Vue2FACodeInput from '@loltech/vue-2fa-code-input';

  const code = ref<string | null>(null);
</script>

<template>
  <div>
    <Vue2FACodeInput v-model="code"/>
  </div>
</template>
```

## Component props

| Property                | Type          | Description                                                                                                                                                                                                                                                                               | Default         |
|-------------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| ```length```            | ```number```  | The 2FA code length.                                                                                                                                                                                                                                                                      | ```6```         |
| ```autofocus```         | ```boolean``` | Whether to autofocus the input.                                                                                                                                                                                                                                                           | ```true```      |
| ```updateImmediately``` | ```boolean``` | By default, the component only updates its ```modelValue``` reference when the code is complete, otherwise it sets it to ```null```. Set this to true to change the behaviour. See the difference live in the [docs](https://lolfactor.github.io/vue3-2fa-code-input/#immediate-updates). | ```false```     |
| ```inputClass```        | ```string```  | Custom CSS class to add to the individual character inputs.                                                                                                                                                                                                                               | ```undefined``` |

## Styling

The component ships with no default styling, but it's pretty straight-forward. The component is just a
container ```div```with an arbitrary number of ```input```s inside. By default, here are only two classes you have to
supply styles for. These are ```vue3-2fa-code-input``` for the container and ```vue3-2fa-code-input-box``` for the
individual inputs.

See a quick example in the [docs](https://lolfactor.github.io/vue3-2fa-code-input/#styling).
