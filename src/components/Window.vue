<template>
  <div class="window selected" :style="windowSize">
    <WindowBar title="Random Window" />
    <div class="white-box"></div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";
import WindowBar from "./WindowBar.vue";

export default defineComponent({
  components: {
    WindowBar,
  },
  props: {
    width: {
      type: String,
      default: "500px",
    },
    height: {
      type: String,
      default: "250px",
    },
  },
  setup(props) {
    const windowSize = {
      width: props.width,
      height: props.height,
    };

    return { windowSize };
  },
});
</script>

<style lang="scss">
@import "~@/assets/scss/_variables.scss";

.selected {
  box-shadow: 0 0 0 1px $selected;
}

.window {
  border: 4px solid $primary-blue;
  border-radius: 8px 8px 0px 0px;
  background-color: $not-quite-white;
  // Edit at run time
  position: fixed;
  top: 50px;
  left: 100px;
}
.white-box {
  width: 50px;
  height: 50px;
  background-color: #fff;
}
</style>
