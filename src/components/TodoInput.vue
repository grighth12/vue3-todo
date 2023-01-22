<template>
  <form @submit.prevent="$emit('submitTodo', value)">
    <input type="text" v-model="value" />
    <input type="submit" />
  </form>
</template>

<script>
import { ref } from "vue";

export default {
  emit: ["submitTodo"],
  setup() {
    const value = ref("");

    return {
      value,
    };
  },
};
</script>
