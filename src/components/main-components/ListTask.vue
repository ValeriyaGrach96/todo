<template>
  <li class="tasks--li">
    <p class="li--id">{{ index + 1 }}.</p>
    <p class="li--title">{{ task.title }}</p>
    <Buttons @remove="removeTask" />
  </li>
</template>

<script>
import Buttons from "./Buttons";

export default {
  name: "ListTask",
  components: {
    Buttons,
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
  },
};
</script>

<style>
li {
  display: flex;
  justify-content: start;

  text-align: center;

  list-style-type: none;
  list-style-position: inside;

  font-size: 15px;

  margin: 0 0 15px 0;
}
p {
  margin-right: 20px;
}
</style>