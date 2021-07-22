<template>
  <div class="window-bar" @drag="onDrag">
    <span>{{ title }}</span>
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
  setup() {
    const onDrag = (evt: MouseEvent) => {
      console.log("DRAGGGGGG", evt);
    };

    return { onDrag };
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
