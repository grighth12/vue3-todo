<template>
  <form class="todo-form" @submit.prevent="submitTodo">
    <div class="todo-form-inner">
      <input
        class="todo-form__input"
        type="text"
        v-model="todoForm.value"
        ref="inputRef"
      />
      <input class="todo-form__submit-button" type="submit" />
    </div>
    <p v-if="todoForm.error" class="todo-form__error-message">
      {{ todoForm.error }}
    </p>
  </form>
</template>

<script>
import { ref, watch, reactive } from "vue";

export default {
  // * emit 명이 native event명과 같은 경우 문제 발생 sumbit(event), submit(value)
  emit: ["submitTodo"],
  setup(props, { emit }) {
    const todoForm = reactive({
      value: "",
      error: "",
    });
    const inputRef = ref();

    watch(inputRef, () => {
      if (inputRef.value) {
        inputRef.value.focus();
      }
    });

    const submitTodo = () => {
      if (!todoForm.value) {
        todoForm.error = "할 일을 입력해주세요";
        return;
      }

      emit("submitTodo", todoForm.value);
      todoForm.value = "";
      todoForm.error = "";
    };

    return {
      todoForm,
      inputRef,
      submitTodo,
    };
  },
};
</script>

<style scoped lang="scss">
.todo-form {
  display: flex;
  flex-direction: column;
  padding: 20px;
  font-size: 18px;
  gap: 4px;

  &-inner {
    display: flex;
    gap: 8px;
  }

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

  &__error-message {
    font-size: 12px;
    color: red;
  }
}
</style>
