<template>
  <TrayBtn :bgColor="lightBlue">
    <span class="maximize-icon"></span>
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
    return { lightBlue: styles.light_blue };
  },
});
</script>

<style lang="scss" scoped>
@import "~@/assets/scss/_variables.scss";

.maximize-icon {
  &::before {
    content: '';
    position: absolute;
    display: block;
    left: 90.8%;
    top: 2.5%;
    width: 16px;
    height: 15px;
    background-color: $not-quite-white;
  }

  &::after {
    content: '';
    position: absolute;
    display: block;
    left: 91.2%;
    top: 3.6%;
    width: 12px;
    height: 11px;
    background-color: $primary-light-blue;
  }
}
</style>