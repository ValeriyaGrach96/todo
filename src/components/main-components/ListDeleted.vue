<template>
  <li class="delete--li">
    <p class="li--id">{{ index + 1 }}</p>
    <p class="li--title">{{ getTask }}</p>
    <Buttons />
  </li>
</template>

<script>
import Buttons from "./Buttons";

export default {
  name: "ListDeleted",
  props: {
    delTask: {
      type: Object,
    },
    index: Number,
  },
  components: {
    Buttons,
  },
  computed: {
    getTask() {
      console.log(this.delTask);
      return this.delTask.title;
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