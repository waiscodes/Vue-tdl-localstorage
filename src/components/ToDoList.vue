<template>
  <div class="tdl">
    <p>{{ yourName }}'s To Do List</p>
  </div>
</template>

<script>
export default {
  name: "ToDoList",
  props: {
    yourName: String,
  },
};
</script>
