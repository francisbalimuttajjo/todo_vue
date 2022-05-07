<template>
  <div class="flex flex-row justify-center align-center">
    <input
      type="checkbox"
      class="mt-2 mr-2"
      :id="id"
      :checked="completed"
      @change="handleChange"
    />
    <h1 :class="{ 'line-through text-red-400': completed }">{{ title }}</h1>
    <h6
      :id="id"
      @click="handleDelete"
      :class="{
        'text-red-500 ml-12 hover:cursor-pointer hover:text-red-700': completed,
        'hidden': !completed,
      }"
    >
      delete
    </h6>
  </div>
</template>
<script>
export default {
  name: "todo-item",
  props: ["title", "completed", "id"],

  setup(props, context) {
    const handleChange = (e) => {
      context.emit("index", e.target.id);
    };
    const handleDelete = (e) => {
    
      context.emit("deleteIndex", e.target.id);
    };
    return {
      handleChange,
      handleDelete,
    };
  },
};
</script>
<style scoped></style>
