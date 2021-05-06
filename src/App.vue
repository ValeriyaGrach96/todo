<template>
  <div id="app">
    <Main
      :todos="todos"
      :deleted="deleted"
      :completed="completed"
      @removeObject="removeObjectOfTodos"
      @addTask="newTask"
      @setDone="setDone"
    />
  </div>
</template>

<script>
import Main from "./components/Main";
import TODO_STATUS from "./helpers";

const LOCAL_STORAGE_KEY = 'LOCAL_STORAGE_KEY';

export default {
  name: "App",
  data() {
    return {
      todos: [],
      deleted: [],
      completed: [],
    };
  },
  components: {
    Main,
  },
  methods: {
    removeObjectOfTodos(id) {
      let taskDeleted = this.todos.find((i) => i.id === id);
      taskDeleted.status = TODO_STATUS[0];
      this.deleted.push(taskDeleted);
      this.todos = this.todos.filter((i) => i.id !== id);
    },
    newTask(newTask) {
      this.todos.push(newTask);
    },
    setDone(id) {
      let taskComplete = this.todos.find((i) => i.id === id);
      taskComplete.status = TODO_STATUS[1];
      this.completed.push(taskComplete);
      this.todos = this.todos.filter((i) => i.id !== id);
    },
  },
  watch: {
    todos(newTodo) {
      console.log(newTodo);
      localStorage.setItem(LOCAL_STORAGE_KEY, JSON.stringify(newTodo));
    }
  },
  mounted () {
    this.todos = JSON.parse(localStorage.getItem(LOCAL_STORAGE_KEY))
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
