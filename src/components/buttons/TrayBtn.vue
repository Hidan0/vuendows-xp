<template>
  <div class="tray-btn" :style="btnStyle">
    <slot></slot>
  </div>
</template>

<script>
import { defineComponent } from "@vue/runtime-core";

export default defineComponent({
  props: {
    bgColor: {
      type: String,
    },
  },
  setup(props) {
    const btnStyle = {
        backgroundColor: props.bgColor,
    };

    return { btnStyle };
  },
});
</script>

<style lang="scss">
@import "~@/assets/scss/_variables.scss";

.tray-btn {
  width: 20px;
  height: 20px;
  border: 2px solid $not-quite-white;
  border-radius: 3px 3px;
  cursor: pointer;
}
</style>
