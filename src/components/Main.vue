<template>
  <div class="page">
    <Header />
    <hr />
    <Input @addTask="task" />
    <MainContent
      :tasks="todos"
      :deletedTask="deleted"
      @removeTodo="removeObject"
      :deleted="deleted"
      :completed="completed"
      @completeTask="completeTask"
    />
  </div>
</template>

<script>
import Header from "./main-components/Header";
import Input from "./main-components/Input";
import MainContent from "./main-components/MainContent";

export default {
  name: "Main",
  components: {
    Header,
    Input,
    MainContent,
  },
  props: {
    todos: Array,
    deleted: Array,
    completed: Array,
  },
  methods: {
    removeObject(id) {
      this.$emit("removeObject", id);
    },
    task(newTask) {
      this.$emit("addTask", newTask);
    },
    completeTask(id) {
      this.$emit('setDone', id)
    }
  },
};
</script>

<style>
.page {
  width: 900px;
  margin: 0 auto;
}
</style>
