<template>
  <div class="w-1/4 self-center mt-20 mx-auto">
    <h3 class="mt-4 font-bold">Todo Application</h3>
    <Input @newTodo="addTodo" />
    <h3 class="mt-4 font-bold">Todo List</h3>
    <div v-for="(todo, index) in todos" :key="index">
      <Todo
        :title="todo.title"
        :completed="todo.completed"
        :id="todo.id"
        @index="handleChange"
        @deleteIndex="removeTodo"
      />
    </div>
  </div>
</template>

<script>
import Input from "./components/Input";
import Todo from "./components/todoItem";
import { ref } from "vue";
export default {
  name: "App",
  components: {
    Input,
    Todo,
  },
  setup() {
    const todos = ref([]);
    const addTodo = (value) => {
      todos.value.push({
        title: value,
        id: new Date().toString(),
        completed: false,
      });
    };
    const handleChange = (val) => {
      todos.value = todos.value.filter((todo) => {
        if (todo.id === val) {
          todo.completed = !todo.completed;
        }
        return todo;
      });
    };

    const removeTodo = (id) => {
      todos.value = todos.value.filter((todo) => todo.id !== id);
    };
    return {
      todos,
      addTodo,
      handleChange,
      removeTodo,
    };
  },
};
</script>

<style></style>
