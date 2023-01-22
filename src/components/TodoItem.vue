<template>
  <li class="todo-item">{{ todo }}</li>
</template>

<script>
export default {
  props: {
    todo: String,
  },
  setup() {},
};
</script>

<style scoped>
.todo-item {
  padding: 5px 20px;
}
</style>
