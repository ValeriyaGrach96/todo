<template>
  <div class="list-tasks">
    <p class="li--id">{{ index + 1 }}.</p>
    <p class="li--title">{{ task.title }}</p>
    <div class="tasks--buttons">
      <Button-execute @onExecute="completeTask"/>
      <Button-clear @onDelete="removeTask"/>
    </div>
  </div>
</template>

<script>
import ButtonClear from './Button-clear.vue';
import ButtonExecute from './Button-execute.vue';

export default {
  name: "ListTask",
  components: {
    ButtonExecute,
    ButtonClear,
  },
  props: {
    task: {
      type: Object,
      required: true,
    },
    index: Number,
  },
  methods: {
    removeTask() {
      this.$emit("removeTask", this.task.id);
    },
    completeTask() {
      this.$emit("completeTask", this.task.id);
    },
  },
};
</script>

<style>
.list-tasks {
  display: flex;
}
.tasks--buttons {
  display: flex;
  text-align: center;
  justify-content: center;
}
.tasks--buttons button {
  width: 25px;
  height: 25px;
  justify-content: center;
}
</style>