<template>
  <TrayBtn class="light-blue">
    <span class="maximize-icon"></span>
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

<style lang="scss" scoped>
@import "~@/assets/scss/_variables.scss";

.light-blue {
  background: $primary-light-blue;
}

.maximize-icon {
  &::before {
    content: "";
    position: relative;
    display: block;
    left: 10%;
    top: 10%;
    width: 16px;
    height: 15px;
    background-color: $not-quite-white;
  }

  &::after {
    content: "";
    position: relative;
    display: block;
    left: 18%;
    top: -52%;
    width: 12px;
    height: 11px;
    background-color: $primary-light-blue;
  }
}
</style>
