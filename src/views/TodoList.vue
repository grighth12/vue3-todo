<template>
  <h1 class="page-title">할 일 목록</h1>
  <TodoInput @submitTodo="handleSubmitTodo" />
  <div>{{ todos }}</div>
</template>

<script>
import TodoInput from "../components/TodoInput.vue";
import { reactive } from "vue";

export default {
  // * export default를 이용할 경우에 components를 등록해주어야 한다
  components: {
    TodoInput,
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
</style>
