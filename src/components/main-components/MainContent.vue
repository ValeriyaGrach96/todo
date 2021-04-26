<template>
  <div class="lists">
    <h2>Список задач</h2>
    <ul class="lists--tasks">
      <ListTask
        v-for="(task, index) of tasks"
        :key="task.id"
        :task="task"
        :index="index"
        @removeTask="removeTodo"
      />
    </ul>
    <h2>Выполненные задачи</h2>
    <ul class="lists--complete">
      <ListComplete />
    </ul>
    <h2>Удаленные задачи</h2>
    <ul class="lists--delete">
      <ListDeleted
        v-for="(task, index) of deleted"
        :key="task.id"
        :delTask="task"
        :index="index"
      />
    </ul>
  </div>
</template>

<script>
import ListTask from "./ListTask";
import ListComplete from "./ListComplete";
import ListDeleted from "./ListDeleted";

export default {
  name: "MainContent",
  components: {
    ListTask,
    ListComplete,
    ListDeleted,
  },
  props: {
    tasks: Array,
    deleted: Array,
  },
  methods: {
    removeTodo(id) {
      this.$emit("removeTodo", id);
    },
  },
};
</script>

<style>
.lists {
  display: flex;
  flex-direction: column;
}
h2 {
  font-size: 1.3em;
  margin: 30px;
}
ul button {
  margin: 0;
  margin-right: 20px;

  width: 30px;
  height: 30px;
}
</style>