<template>
    <button
      type="button"
      class="buttons--button-task"
      aria-label="Выполнить действие"
      @click="$emit('onExecute')"
    >
      <img
        class="button-task--img"
        src="../../image/icon-task.svg"
        alt="Галочка"
      />
    </button>
</template>

<script>
export default {
  name: "ButtonExecute",
};
</script>

<style>
button {
  padding: 0;
  margin: 0;
  height: 100%;
  width: 100%;

  background: transparent;
  border: none;
  border-radius: 50%;
}
button:focus {
  outline: none;
  box-shadow: 0px 0px 4px 2px rgba(0, 94, 106, 0.44);
}
.button-task--img {
  width: 100%;
  height: 100%;
  line-height: 100%;
}
</style>
