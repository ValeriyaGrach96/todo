<template>
  <div class="list-complete">
    <p class="li--id">{{index + 1}}</p>
    <p class="li--title">{{copmleteTask.title}}</p>
    <div class="complete--buttons">
      <Button-clear @onDelete="removeTask"/>
    </div>
  </div>
</template>

<script>
import ButtonClear from './Button-clear.vue'

export default {
  name: "ListComplete",
  components: {
    ButtonClear,
  },
  props: {
    copmleteTask:{
      type: Object,
      required: true,
    },
    index: Number,
  },
  methods: {
    removeTask() {
      this.$emit("removeTask", this.copmleteTask.id);
    }
  }
};
</script>

<style>
.list-complete {
  display: flex;
}
.complete--buttons {
  display: flex;
  text-align: center;
  justify-content: center;
}
.complete--buttons button {
  width: 25px;
  height: 25px;
  justify-content: center;
}
</style>