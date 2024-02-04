<script setup lang="ts">
import { ref } from 'vue';

interface Props {
  length?: number;
  autofocus?: boolean;
  inputClass?: string;
  updateImmediately?: boolean;
  modelValue: string | null;
}

const props = withDefaults(defineProps<Props>(), {
  length: 6,
  autofocus: true,
  updateImmediately: false,
});

const emit = defineEmits<{ (e: 'update:modelValue', value: string | null): void }>();

const indexArray = [...(new Array(props.length).keys())];
const container = ref<HTMLDivElement | null>(null);
const refs: Array<HTMLInputElement> = [];

function assignRef(element: HTMLInputElement, index: number) {
  refs[index] = element;
}

function onPaste(event: ClipboardEvent) {
  event.preventDefault();

  const content = event.clipboardData?.getData('text/plain');
  if (content !== undefined && content.length === props.length) {
    indexArray.forEach((index) => refs[index].value = content[index]);
    refs[props.length - 1].focus();
    emit('update:modelValue', content);
  }
}

function onFocusIn() {
  const firstEmpty = refs.find((element) => element.value.length === 0);
  if (firstEmpty !== undefined) {
    firstEmpty.focus();
  } else {
    refs[props.length - 1]?.focus();
  }
}

function onInput(index: number) {
  if (index < props.length - 1) {
    refs[index + 1].focus();
    if (props.updateImmediately) {
      emit('update:modelValue', refs.map((element) => element.value).join(''));
    }
  } else {
    refs[index].value = refs[index].value.substring(0, 1);
    emit('update:modelValue', refs.map((element) => element.value).join(''));
  }
}

function onKeyDown(event: KeyboardEvent, index: number) {
  switch (event.key) {
    case 'ArrowLeft':
    case 'ArrowRight':
      event.preventDefault();
      break;
    case 'Backspace':
      if (refs[index].value.length > 0) {
        refs[index].value = '';
      } else if (index > 0) {
        refs[index - 1].value = '';
        refs[index - 1].focus();
      }

      let code: string | null = refs.map((element) => element.value).join('');
      if (code.length === 0) {
        code = null;
      }
      if (props.updateImmediately) {
        emit('update:modelValue', code);
      } else {
        emit('update:modelValue', null);
      }
      break;
    default:
      return true;
  }
}
</script>

<template>
  <div ref="container" class="vue3-2fa-code-input">
    <input type="text" class="vue3-2fa-code-input-box" :class="props.inputClass"
           v-for="index in indexArray" :key="index"
           :ref="(element) => assignRef((element as HTMLInputElement), index)"
           @paste.prevent="onPaste" @focusin.prevent="onFocusIn"
           @input.prevent="onInput(index)" @keydown="onKeyDown($event, index)"
           :autofocus="props.autofocus && index === 0">
  </div>
</template>
