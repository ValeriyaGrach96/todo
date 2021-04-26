<template>
  <div class="page">
    <Header />
    <hr />
    <Input @addTask="task" />
    <MainContent
      :tasks="Todos"
      :deletedTask="deleted"
      @removeTodo="removeObject"
      :deleted="deleted"
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
    Todos: Array,
    deleted: Array,
  },
  methods: {
    removeObject(id) {
      this.$emit("removeObject", id);
    },
    task(newTask) {
      this.$emit("addTask", newTask);
    },
  },
};
</script>

<style>
.page {
  width: 900px;
  margin: 0 auto;
}
</style>
