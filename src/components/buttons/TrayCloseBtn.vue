<template>
  <TrayBtn :bgColor="danger">
    <span class="close-icon"> </span>
  </TrayBtn>
</template>

<script>
import { defineComponent } from "@vue/runtime-core";
import TrayBtn from "./TrayBtn.vue";

import styles from "../../assets/scss/_variables.scss";

export default defineComponent({
  components: {
    TrayBtn,
  },
  setup() {
    return { danger: styles.danger };
  },
});
</script>

<style lang="scss" scoped>
@import "~@/assets/scss/_variables.scss";

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
