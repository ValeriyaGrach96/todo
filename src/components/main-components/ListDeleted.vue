<template>
  <div class="list-delete">
    <p class="li--id">{{ index + 1 }}</p>
    <p class="li--title">{{ delTask.title }}</p>
    <div class="delete--buttons">
      <Button-clear @onDelete="deleteTask"/>
    </div>
  </div>
</template>

<script>
import ButtonClear from './Button-clear.vue';

export default {
  name: "ListDeleted",
    components: {
      ButtonClear,
  },
  props: {
    delTask: {
      type: Object,
    },
    index: Number,
  },
  methods: {
    deleteTask() {
      this.$emit('deleteTask', this.delTask.id);
    }
  }
};
</script>

<style>
.list-delete {
  display: flex;
}
.delete--buttons {
  display: flex;
  text-align: center;
  justify-content: center;
}
.delete--buttons button {
  width: 25px;
  height: 25px;
  justify-content: center;
}
.list-delete .li--title {
  text-decoration: line-through;
}
</style>