<template>
  <TrayBtn class="light-blue">
    <span class="hide-icon"></span>
  </TrayBtn>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";
import TrayBtn from "./TrayBtn.vue";
export default defineComponent({
  components: {
    TrayBtn,
  },
});
</script>

<style lang="scss">
@import "~@/assets/scss/_variables.scss";

.light-blue {
  background: $primary-light-blue;
}

.hide-icon {
  position: relative;
  top: 62%;
  left: 10%;
  display: block;
  background: $not-quite-white;
  width: 10px;
  height: 4px;
}
</style>