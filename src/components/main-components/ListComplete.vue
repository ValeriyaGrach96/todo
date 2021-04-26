<template>
  <li class="complete--li">
    <p class="li--id"></p>
    <Buttons />
  </li>
</template>

<script>
import Buttons from "./Buttons";

export default {
  name: "ListComplete",
  components: {
    Buttons,
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