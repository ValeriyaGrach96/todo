<template>
  <div id="app">
    <Main
      :todos="todos"
      :deleted="deleted"
      @removeObject="removeObjectOfTodos"
      @addTask="newTask"
    />
  </div>
</template>

<script>
import Main from "./components/Main";
import jj from "./helpers";

export default {
  name: "App",
  data() {
    return {
      todos: [
        { id: 1, title: "Buy bread", status: jj[2] },
        { id: 2, title: "Buy milk", status: jj[2] },
        { id: 3, title: "Buy tomato", status: jj[2] },
      ],
      deleted: [],
    };
  },
  components: {
    Main,
  },
  methods: {
    removeObjectOfTodos(id) {
      let taskDeleted = this.todos.find((i) => i.id === id);
      taskDeleted.status = jj[0];
      this.deleted.push(taskDeleted);
      this.todos = this.todos.filter((i) => i.id !== id);
    },
    newTask(newTask) {
      this.todos.push(newTask);
    },
  },
};
</script>

<style>
#app * {
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 0px;

  background-color: rgb(255, 252, 249);
}
</style>
