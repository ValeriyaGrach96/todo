<template>
  <form class="page--form" @submit.prevent="onSubmit">
    <input
      type="text"
      placeholder="Введите текст задачи"
      class="form--input"
      v-model="title"
    />
    <div class="input--buttons">
      <ButtonExecute @onExecute="createTask"/>
      <ButtonClear @onDelete="onDelete"/>
    </div>
  </form>
</template>

<script>
import TODO_STATUS from "../../helpers";
import ButtonClear from './ButtonClear.vue';
import ButtonExecute from './ButtonExecute.vue';

export default {
  name: "Input",
  components: {
    ButtonClear,
    ButtonExecute,
  },
  data() {
    return {
      title: "",
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        this.$emit("addTask", {
          id: Date.now(),
          title: this.title,
          status: TODO_STATUS[2],
        });
        this.onDelete();
      }
    },
    onDelete() {
      this.title = "";
    },
    createTask() {
      this.onSubmit();
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
.input--buttons {
  display: flex;
}
.input--buttons button {
  width: 45px;
  height: 45px;
}
button + button {
  margin-left: 10px;
}
</style>
