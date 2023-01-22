<template>
  <form @submit.prevent="submitTodo">
    <input type="text" v-model="todo" ref="inputRef" />
    <input type="submit" />
  </form>
</template>

<script>
import { ref, watch } from "vue";

export default {
  // * emit 명이 native event명과 같은 경우 문제 발생 sumbit(event), submit(value)
  emit: ["submitTodo"],
  setup(props, { emit }) {
    const todo = ref("");
    const inputRef = ref();

    watch(inputRef, () => {
      if (inputRef.value) {
        inputRef.value.focus();
      }
    });

    const submitTodo = () => {
      emit("submitTodo", todo.value);
      todo.value = "";
    };

    return {
      todo,
      inputRef,
      submitTodo,
    };
  },
};
</script>
