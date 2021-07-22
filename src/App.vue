<template>
  <Window width="700px" height="400px" />
</template>

<script lang="ts">
import Window from "./components/Window.vue";

export default {
  name: "App",
  components: {
    Window,
  },
};
</script>

<style>
* {
  padding: 0px;
  margin: 0px;
}
body {
  background-color: #3b4252;
}
#app {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
  background-image: url("./assets/img/bg.jpg");
}
</style>
