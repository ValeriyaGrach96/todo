<template>
  <div class="lists">
    <ListsTasks
      v-if="states.opened.status"
      :tasks="tasks"
      :statusLists="'opened'"
      @completeTask="completeTask"
      @deleteTask="deleteTask"
    >
      <template #header>
        <h2>{{states.opened.nameList}}</h2>
      </template>
    </ListsTasks>
    <ListsTasks
      v-if="states.completed.status"
      :tasks="tasks"
      :statusLists="'completed'"
      @completeTask="completeTask"
      @deleteTask="deleteTask"
    >
      <template #header>
        <h2>{{states.completed.nameList}}</h2>
      </template>
    </ListsTasks>
    <ListsTasks
      v-if="states.deleted.status"
      :tasks="tasks"
      :statusLists="'deleted'"
      @completeTask="completeTask"
      @deleteTaskFromLocalStorage="deleteTaskFromLocalStorage"
    >
      <template #header>
        <h2>{{states.deleted.nameList}}</h2>
      </template>
    </ListsTasks>
  </div>
</template>

<script>
import ListsTasks from "./ListsTasks"

export default {
  name: "MainContent",
  components: {
    ListsTasks,
  },
  props: {
    tasks: Array,
    states: Object,
  },
  methods: {
    completeTask(id) {
      this.$emit('completeTask', id)
    },

    deleteTask(id) {
      this.$emit('deleteTask', id);
    },

    deleteTaskFromLocalStorage(id) {
      this.$emit("delTaskFromLocalStorage", id);
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
  margin: 20px 30px 0px;
}
</style>