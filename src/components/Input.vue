<template>
  <div class="flex flex-row self-center mt-5 mx-auto">
    <input
      class="border border-green-200 px-2"
      type="text"
      v-model="inputValue"
      placeholder="add todo"
    />
    <button
      class="bg-blue-500 hover:bg-blue-400 rounded-sm px-3 text-white text-bold"
      @click="submitTodo"
    >
      add
    </button>
  </div>
</template>
<script>
import { ref } from "vue";
export default {
  name: "todo-input",
  setup(props, context) {
    const inputValue = ref("");
    const submitTodo = () => {
      context.emit("newTodo", inputValue.value);
      inputValue.value = "";
    };
    return {
      submitTodo,
      inputValue,
    };
  },
  emits: ["newTodo"],
};
</script>
<style scoped></style>
