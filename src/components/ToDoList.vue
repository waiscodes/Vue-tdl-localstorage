<template>
  <div class="tdl">
    <p>{{ yourName }}'s To Do List</p>
    <form>
      <label for="input"></label>
      <input type="text" name="input" id="input" />
      <input type="submit" value="Add To List" />
    </form>
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

<style scoped>
.tdl {
  border: solid;
}
</style>
