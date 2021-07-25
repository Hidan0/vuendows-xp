<template>
  <div class="window-bar">
    <span class="text">{{ title }}</span>
    <div class="tray">
      <HideBtn /><MaximizeBtn class="mg-left" /><CloseBtn class="mg-left" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";

import HideBtn from "./buttons/TrayHideBtn.vue";
import CloseBtn from "./buttons/TrayCloseBtn.vue";
import MaximizeBtn from "./buttons/TrayMaximizeBtn.vue";

export default defineComponent({
  components: {
    HideBtn,
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
  background-image: linear-gradient(to right, $primary-blue, $primary-light-blue, $primary-blue);

  &::before {
    position: absolute;
    top: -2px;
    content: "";
    width: 99%;
    height: 2px;
    background: rgba($color: #fff, $alpha: 0.15);
  }

  & > span {
    padding: 0px 2px;
    justify-content: center;
    color: #fff;
    user-select: none;
  }

  &:hover {
    cursor: pointer;
  }
}

.tray {
  display: flex;
}
.mg-left {
  margin-left: 2px;
}
</style>
