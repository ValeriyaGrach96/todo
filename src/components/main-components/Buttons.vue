<template>
  <div class="buttons">
    <button
      type="submit"
      class="buttons--button-task"
      aria-label="Выполнить действие"
      @click="$emit('onSubmit')"
    >
      <img
        class="button-task--img"
        src="../../image/icon-task.svg"
        alt="Галочка"
      />
    </button>
    <button
      type="button"
      class="buttons--button-clear"
      aria-label="Удалить"
      @click="$emit('onRemove')"
    >
      <img
        class="button-clear--img"
        src="../../image/icon-clear.svg"
        alt="Крестик"
      />
    </button>
  </div>
</template>

<script>
export default {
  name: "Buttons",
};
</script>

<style>
.buttons {
  margin: auto 0;
}
button {
  padding: 0;
  margin-right: 20px;

  background: transparent;
  border: none;
  border-radius: 50%;
}
button:focus {
  outline: none;
  box-shadow: 0px 0px 4px 2px rgba(0, 94, 106, 0.44);
}
</style>
