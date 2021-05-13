<template>
  <div class="list-tasks">
    <p class="li--id">{{ index + 1 }}.</p>
    <p class="li--title">{{ task.title }}</p>
    <div class="tasks--buttons">
      <ButtonExecute v-if="statusLists === 'opened'" @onExecute="completeTask"/>
      <ButtonClear @onDelete="removedTask"/>
    </div>
  </div>
</template>

<script>
import ButtonClear from './ButtonClear.vue';
import ButtonExecute from './ButtonExecute.vue';

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
    statusLists: String,
  },
  methods: {
    removedTask() {
      this.$emit("removedTask", this.task.id);
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