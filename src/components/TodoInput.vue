<template>
  <form class="todo-form" @submit.prevent="submitTodo">
    <input class="todo-form__input" type="text" v-model="todo" ref="inputRef" />
    <input class="todo-form__submit-button" type="submit" />
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

<style scoped lang="scss">
.todo-form {
  display: flex;
  gap: 8px;
  padding: 20px;
  font-size: 18px;

  &__input {
    width: 80%;
    padding: 10px;
    border-radius: 4px;

    &:focus,
    &:focus-within,
    &:focus-visible {
      outline: 1px solid orange;
    }
  }

  &__submit-button {
    padding: 10px 20px;
    font-weight: 500;
    background-color: orange;
    border: 0;
    border-radius: 4px;
    color: white;
  }
}
</style>
