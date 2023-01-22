<template>
  <h1 class="page-title">할 일 목록</h1>
  <TodoInput @submitTodo="handleSubmitTodo" />

  <ul>
    <TodoItem v-for="todo in todos" :key="todo" :todo="todo" />
  </ul>
</template>

<script>
import TodoInput from "../components/TodoInput.vue";
import TodoItem from "../components/TodoItem.vue";
import { reactive } from "vue";

export default {
  // * export default를 이용할 경우에 components를 등록해주어야 한다
  components: {
    TodoInput,
    TodoItem,
  },
  setup() {
    const todos = reactive([]);

    const handleSubmitTodo = (value) => {
      todos.push(value);
    };

    return {
      todos,
      handleSubmitTodo,
    };
  },
};
</script>

<style scoped>
.page-title {
  font-size: 40px;
  font-weight: 700;
  margin-bottom: 16px;
}

ul {
  list-style: inside;
}
</style>
