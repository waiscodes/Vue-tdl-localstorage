<template>
  <div class="tdl">
    <h2>{{ yourName }}'s To Do List</h2>
    <form>
      <label for="input"></label>
      <input type="text" name="input" id="input" />
      <input type="submit" value="Add To List" />
    </form>
    <ul>
      <li></li>
    </ul>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "ToDoList",
  props: {
    yourName: String,
  },

  setup() {
    const newToDo = ref("");
    const defaultData = [
      {
        done: false,
        content: "Read a book",
      },
    ];
    const toDosData = JSON.parse(localStorage.getItem("todos")) || defaultData;
    const toDos = ref(toDosData);

    return {
      newToDo,
      toDos,
    };
  },
};
</script>

<style scoped>
.tdl {
  border: solid;
}
ul li {
  display: block;
}
</style>
