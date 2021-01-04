<template>
  <div class="tdl">
    <h2>{{ yourName }}'s To Do List</h2>
    <form action="#" @submit.prevent="addToDo">
      <label for="input">New To Do</label>
      <input
        type="text"
        name="input"
        id="input"
        v-model="newToDo"
        autocomplete="off"
      />
      <input type="submit" value="Add To List" />
    </form>
    <ul>
      <li v-for="(item, index) in toDos" :key="index">
        <span>{{ item.content }}</span>
        <span>
          <button @click="doneToDo(index)">Done</button>
          <button @click="removeToDo(index)">Delete</button>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "ToDoList",
  props: {
    yourName: {
      type: String,
      required: true,
    },
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

    const addToDo = () => {
      toDos.value.unshift({
        done: false,
        content: newToDo.value,
      });
      newToDo.value = "";
    };

    const removeToDo = () => {
      console.log("Deleted");
    };

    const doneToDo = () => {
      console.log("Done");
    };

    const saveData = () => {
      const storageData = JSON.stringify(toDos.value);
      localStorage.setItem("todos", storageData);
    };

    return {
      newToDo,
      toDos,
      addToDo,
      saveData,
      removeToDo,
      doneToDo,
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
  display: flex;
  justify-content: space-between;
  margin: 5px;
  padding: 0px;
}

ul {
  padding: 0px;
}
</style>
