<template>
  <div>
    <slot name="header"></slot>
    <ul class="lists--tasks">
      <li
        class="tasks--li"
        v-for="(task, index) of filterTasks"
        :key="task.id"
      >
        <ListItemTask
          :task="task"
          :statusLists="statusLists"
          :index="index"
          @completeTask="completeTask"
          @removedTask="removedTask"
        />
      </li>
    </ul>
  </div>
</template>

<script>
import TODO_STATUS from "../../helpers/index"
import ListItemTask from './ListItemTask'

export default {
  name: "ListsTasks",
  components: {
    ListItemTask,
  },
  props: {
    tasks: Array,
    statusLists: String,
  },
  computed: {
    filterTasks () {
      return this.tasks.filter(item => item.status === this.statusLists);
    },
  },
  methods: {
    completeTask(id) {
      this.$emit("completeTask", id);
    },

    removedTask(id) {
      if (this.statusLists === TODO_STATUS[0]) {
        this.$emit('deleteTaskFromLocalStorage', id);
      } else {
        this.$emit('deleteTask', id);
      }
    },
  }
}
</script>


<style>
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