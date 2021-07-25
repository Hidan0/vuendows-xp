<template>
  <Window width="700px" height="400px" :x="200" :y="200">
    <h1>Hello World</h1>
  </Window>
  <TaskBar />
</template>

<script lang="ts">
import Window from "./components/Window.vue";
import TaskBar from "./components/Taskbar.vue";

export default {
  name: "App",
  components: {
    Window,
    TaskBar,
  },
};
</script>

<style lang="scss">
@import "~@/assets/scss/_variables.scss";

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
.text {
  color: $not-quite-white;
  text-shadow: 0 0 3px black;
}
</style>
