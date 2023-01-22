<template>
  <h1 class="page-title">할 일 목록</h1>
  <TodoInput @submitTodo="handleSubmitTodo" />

  <ol>
    <TodoItem
      v-for="(todo, index) in todos"
      :key="todo"
      :todo="todo"
      @removeTodo="() => handleRemoveTodo(index)"
    />
  </ol>
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

    const handleRemoveTodo = (index) => {
      todos.splice(index, 1);
    };

    return {
      todos,
      handleSubmitTodo,
      handleRemoveTodo,
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

ol {
  padding: 20px;
  margin: auto;
  list-style: decimal;
}
</style>
