<template>
  <header class="page--header">
    <h1>TodoList</h1>
    <div class="header--numbers">
      <p class="numbers-quantity">N</p>
      <p class="numbers-non">n</p>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>


<style scoped>
.page--header {
  display: flex;
  justify-content: space-between;

  height: 100px;
}
h1 {
  margin: auto 0 0 30px;
}
.header--numbers {
  position: relative;

  margin: auto 30px 0 0;
}
.numbers-non {
  position: absolute;
  top: -10px;
  left: 65%;
  margin: 0;

  width: 30px;
  height: 30px;
  border-radius: 50%;

  color: azure;
  line-height: 30px;
  text-align: center;
  font-size: 20px;

  background-color: rgb(0, 112, 112);
}
.numbers-quantity {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  margin: 0;

  color: #2c3e50;
  line-height: 60px;
  text-align: center;
  font-size: 20px;

  background-color: rgb(75, 148, 148);
}
</style>>

