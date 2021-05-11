<template>
  <div class="page">
    <Header :amountTasks="todos.length"
            :amountOfComplete="amountOfComplete"/>
    <hr />
    <Input @addTask="addTask" />
    <MainContent
      :tasks="todos"
      @delTaskFromTodo="delTaskFromTodo"
      @amountTasks="amountTasks"
    />
  </div>
</template>

<script>
import Header from "./main-components/Header";
import Input from "./main-components/Input";
import MainContent from "./main-components/MainContent";

const LOCAL_STORAGE_KEY = 'TODO_LIST';

export default {
  name: "Main",
  components: {
    Header,
    Input,
    MainContent,
  },
  data() {
    return {
      todos: [],
      amountOfComplete: 0,
    }
  },
  methods: {
    addTask(newTask) {
      this.todos.push(newTask);
    },
    delTaskFromTodo(id) {
      this.todos = this.todos.filter(task => task.id !== id);
    },
    amountTasks(number) {
      this.amountOfComplete = number;
    }
  },
  watch: {
    todos(newTodo) {
      this.todos = this.todos || [];
      localStorage.setItem(LOCAL_STORAGE_KEY, JSON.stringify(newTodo));
    },
  },
  mounted () {
    this.todos = JSON.parse(localStorage.getItem(LOCAL_STORAGE_KEY))
  },
  updated () {

    console.log('updated',this.todos)
  }
};
</script>

<style>
.page {
  width: 900px;
  margin: 0 auto;

  background-color: rgb(227, 255, 250);
}
</style>
