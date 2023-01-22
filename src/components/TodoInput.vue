<template>
  <form @submit.prevent="$emit('submitTodo', value)">
    <input type="text" v-model="value" ref="inputRef" />
    <input type="submit" />
  </form>
</template>

<script>
import { ref, watch } from "vue";

export default {
  // * emit 명이 native event명과 같은 경우 문제 발생 sumbit(event), submit(value)
  emit: ["submitTodo"],
  setup() {
    const value = ref("");
    const inputRef = ref();

    watch(inputRef, () => {
      if (inputRef.value) {
        inputRef.value.focus();
      }
    });

    return {
      value,
      inputRef,
    };
  },
};
</script>
