<template>
  <li class="todo-item">
    <div class="todo-item-inner">
      <span>{{ todo }}</span>

      <button class="todo-item__remove-button" @click="$emit('removeTodo')">
        삭제
      </button>
    </div>
  </li>
</template>

<script>
export default {
  emit: ["removeTodo"],
  props: {
    todo: String,
  },
  setup() {},
};
</script>

<style scoped lang="scss">
.todo-item {
  height: max-content;
  padding: 10px 15px;
  &-inner {
    display: flex;
    justify-content: space-between;
  }

  &__remove-button {
    padding: 4px;
    color: white;
    background-color: red;
    border: 0;
    border-radius: 4px;

    :focus-visible {
      outline: 1px solid white;
    }
  }
}
</style>
