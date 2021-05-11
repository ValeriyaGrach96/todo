<template>
  <div class="lists">
    <h2>Список задач</h2>
    <ul class="lists--tasks">
      <li class="tasks--li"
          v-for="(task, index) of filterTasks"
          :key="task.id">
        <ListTask :task="task"
                  :index="index"
                  @completeTask="completeTask"
                  @removeTask="removeTask"/>
      </li>
    </ul>
    <h2>Выполненные задачи</h2>
    <ul class="lists--complete">
      <li class="complete--li"
          v-for="(task, index) of completedTasks"
          :key="task.id">
        <ListComplete :copmleteTask="task"
                      :index="index"
                      @removeTask="removeTask"/>
      </li>
    </ul>
    <h2>Удаленные задачи</h2>
    <ul class="lists--delete">
      <li class="delete--li"
          v-for="(task, index) of deletedTasks"
          :key="task.id">
        <ListDeleted :delTask="task"
                     :index="index"
                     @deleteTask="delTaskFromTodo"/>
      </li>
    </ul>
  </div>
</template>

<script>
import ListTask from "./ListTask";
import ListComplete from "./ListComplete";
import ListDeleted from "./ListDeleted";

import TODO_STATUS from "../../helpers/index";

export default {
  name: "MainContent",
  components: {
    ListTask,
    ListComplete,
    ListDeleted,
  },
  props: {
    tasks: Array,
  },
  methods: {
    removeTask(id) {
      const removeTask = this.tasks.find(task => task.id === id);
      removeTask.status = TODO_STATUS[0];
    },
    completeTask(id) {
      const completeTask = this.tasks.find(task => task.id === id);
      completeTask.status = TODO_STATUS[1];
    },
    delTaskFromTodo(id) {
      this.$emit("delTaskFromTodo", id);
    }
  },
  computed: {
    filterTasks() {
      return this.tasks.filter(task => task.status === "open");
    },
    completedTasks() {
      const completed = this.tasks.filter(task => task.status === "completed");
      let number = completed.length;
      this.$emit("amountTasks", number);
      return completed;
    },
    deletedTasks() {
      return this.tasks.filter(task => task.status === "deleted");
    },
  }
};
</script>

<style>
.lists {
  display: flex;
  flex-direction: column;
}
h2 {
  font-size: 1.3em;
  margin: 20px 30px 0px;
}
ul button {
  margin: 0;
  margin-right: 10px;

  width: 30px;
  height: 30px;
}
ul p {
  margin: 0;
  margin-right: 10px;
  line-height: 25px;
}
li {
  display: flex;
  flex-direction: row;

  text-align: center;

  list-style-type: none;
  list-style-position: inside;

  font-size: 15px;
}
li + li {
  margin-top: 10px;
}
</style>