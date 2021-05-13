<template>
  <div id="app">
    <Main/>
  </div>
</template>

<script>
import Main from "./components/Main";

export default {
  name: "App",
  components: {
    Main,
  },
}
</script>

<style>
#app * {
  box-sizing: border-box;
}
#app {
  display: flex;
  flex-direction: column;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 0px;
}
</style>
