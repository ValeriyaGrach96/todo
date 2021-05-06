<template>
  <form class="page--form" @submit.prevent="onSubmit">
    <input
      type="text"
      placeholder="Введите текст задачи"
      class="form--input"
      v-model="title"
    />
    <Buttons @onRemove="onRemove"/>
  </form>
</template>

<script>
import Buttons from "./Buttons";
import jj from "../../helpers";

export default {
  name: "Input",
  components: {
    Buttons,
  },
  data() {
    return {
      title: "",
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTask = {
          id: Date.now(),
          title: this.title,
          status: jj[2],
        };
        this.$emit("addTask", newTask);
        this.title = "";
      }
    },
    onRemove() {
      this.title = "";
    }
  },
};
</script>

<style>
.page--form {
  display: flex;

  margin-top: 30px;
}
.form--input {
  margin: 0 30px;
  padding: 10px;

  width: 70%;

  font-size: 20px;

  border: 1px solid #2c3e50af;
  border-radius: 10px;
}
.form--input:focus {
  outline: none;

  border: 3px solid #2c3e50af;
  border-radius: 10px;
}
.page--form img {
  width: 45px;
  height: 45px;
}
</style>
