<template>
  <TrayBtn class="danger">
    <span class="close-icon"> </span>
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

.danger {
  background: $danger;
}

.close-icon {
  margin-right: 0.1em;

  &::before,
  &::after {
    position: fixed;
    content: "";
    height: 20px;
    width: 2px;
    background-color: $not-quite-white;
  }

  &::before {
    transform: rotate(45deg);
  }

  &::after {
    transform: rotate(-45deg);
  }
}
</style>
