<template>
  <div class="window-bar">
    <span>{{ title }}</span>
    <div class="tray"><MaximizeBtn class="mg-left" /><CloseBtn class="mg-left" /></div>
  </div>
</template>

<script>
import { defineComponent } from "@vue/runtime-core";
import CloseBtn from "./buttons/TrayCloseBtn.vue";
import MaximizeBtn from "./buttons/TrayMaximizeBtn.vue";

export default defineComponent({
  components: {
    CloseBtn,
    MaximizeBtn,
  },
  props: {
    title: {
      type: String,
    },
  },
});
</script>

<style lang="scss">
@import "~@/assets/scss/_variables.scss";

.window-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 28px;
  background-color: $primary-blue;

  & > span {
    padding: 0px 2px;
    justify-content: center;
    color: #fff;
  }
}

.tray {
  display: flex;
}
.mg-left {
    margin-left: 2px;
}
</style>
