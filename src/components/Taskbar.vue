<template>
  <div class="bar">
    <div class="start-menu text">
      <span class="start-menu-img"></span> Start
    </div>
    <div class="tray">
      <div class="expand-btn text">˂</div>
      <span class="text">{{ time }}</span>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";
import { ref } from "vue";

export default defineComponent({
  setup: () => {
    function formatNum(num: number): string {
      return num <= 9 ? 0 + num.toString() : num.toString();
    }

    const time = ref("");

    const getDate = () => {
      const current = new Date();
      time.value =
        formatNum(current.getHours()) + ":" + formatNum(current.getMinutes());

      time.value += " " + current.toDateString();
    };

    getDate();
    setInterval(getDate, 1000);

    return { time };
  },
});
</script>

<style lang="scss">
@import "~@/assets/scss/_variables.scss";

.bar {
  position: absolute;
  display: flex;
  align-items: center;
  justify-content: space-between;
  bottom: 0;
  height: 32px;
  width: 100%;
  background: $primary-blue;
  box-shadow: inset 0 4px 1px lighten($color: $primary-blue, $amount: 10%),
    inset 0 -4px 3px darken($color: $primary-blue, $amount: 10%);

  & > .tray {
    display: flex;
    align-items: center;
    width: max-content;
    height: inherit;
    background: $primary-light-blue;
    box-shadow: inset 0 4px 1px
        lighten($color: $primary-light-blue, $amount: 10%),
      inset 0 -4px 3px darken($color: $primary-light-blue, $amount: 10%);

    & > .expand-btn {
      position: relative;
      cursor: pointer;
      box-sizing: border-box;
      left: -10px;
      width: 16px;
      height: 16px;
      border-radius: 50%;
      color: white;
      font-weight: bolder;
      box-shadow: 0 0 2px black;
      background-image: linear-gradient(
        110deg,
        lighten($color: $primary-light-blue, $amount: 15%) 10%,
        $primary-blue 90%
      );
    }
  }

  & > .start-menu {
    display: flex;
    align-items: center;
    cursor: pointer;
    width: 110px;
    height: inherit;
    background: $success;
    border-radius: 0px 12px 12px 0px;
    color: $not-quite-white;
    font-weight: bold;
    font-style: italic;
    box-shadow: inset 0 0 12px rgba($color: #000, $alpha: 0.6),
      inset 0 4px 1px rgba($color: #fff, $alpha: 0.4);

    & > .start-menu-img {
      width: 24px;
      height: 24px;
      background-image: url("../assets/img/w-logo.png");
      background-size: cover;
      margin-left: 10px;
      margin-right: 5px;
    }
  }
}
</style>