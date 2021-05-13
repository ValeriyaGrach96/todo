<template>
  <div class="page">
    <Header :amountTasks="todos.length" :amountOfComplete="amountOfComplete" />
    <hr />
    <Input @addTask="addTask" />
    <MainContent
      :tasks="todos"
      :states="states"
      @deleteTask="deleteTask"
      @delTaskFromLocalStorage="delTaskFromLocalStorage"
      @completeTask="completeTask"
    />
  </div>
</template>

<script>
import TODO_STATUS from "../helpers/index";
import Header from "./main-components/Header";
import Input from "./main-components/Input";
import MainContent from "./main-components/MainContent";

const LOCAL_STORAGE_KEY = "TODO_LIST";

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
      states: {
        opened: {
          status: false,
          nameList: "Список задач",
        },
        completed: {
          status: false,
          nameList: "Выполненные задачи",
        },
        deleted: {
          status: false,
          nameList: "Удаленные задачи",
        },
      },
    };
  },

  watch: {
    todos(newTodo) {
      this.todos = this.todos || [];
      this.changeState();
      localStorage.setItem(LOCAL_STORAGE_KEY, JSON.stringify(newTodo));
    },
  },

  mounted() {
    this.todos = JSON.parse(localStorage.getItem(LOCAL_STORAGE_KEY));
  },

  methods: {
    addTask(newTask) {
      this.todos.push(newTask);
    },

    delTaskFromLocalStorage(id) {
      this.todos = this.todos.filter((task) => task.id !== id);
    },

    completeTask(id) {
      const indexToComplete = this.todos.findIndex((item) => item.id === id);
      this.todos.splice(indexToComplete, 1, {
        ...this.todos[indexToComplete],
        status: TODO_STATUS[1]
      });

      this.amountOfComplete = this.todos.filter((item) => item.id === id).length;
    },

    deleteTask(id) {
      const indexToDelete = this.todos.findIndex((item) => item.id === id);
      this.todos.splice(indexToDelete, 1, {
        ...this.todos[indexToDelete],
        status: TODO_STATUS[0]
      });
    },

    changeState() {
      if (this.todos.length) {
        const hasOpenTask = this.todos.some(item => item.status === TODO_STATUS[2]);
        const hasCompleteTask = this.todos.some(item => item.status === TODO_STATUS[1]);
        const hasDeletedTak = this.todos.some(item => item.status === TODO_STATUS[0]);

        this.states.opened.status = hasOpenTask;
        this.states.completed.status = hasCompleteTask;
        this.states.deleted.status = hasDeletedTak;
      }
    },
  },
};
</script>

<style>
.page {
  width: 900px;
  margin: 0 auto;

  background-color: rgb(227, 255, 250);
}
</style>