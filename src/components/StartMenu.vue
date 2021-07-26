<template>
  <div class="menu-window">
    <div class="menu-top-bar">
      <div class="profile-img" :style="bgImg"></div>
      <span class="text">Jeff</span>
    </div>
    <slot></slot>
    <div class="menu-bottom-bar"></div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";

export default defineComponent({
  props: {},
});
</script>

<style lang="scss">
@import "~@/assets/scss/_variables.scss";

.menu-window {
  position: fixed;
  width: 560px;
  height: 620px;
  left: 0px;
  background: #fff;
  // border-right: 4px solid $primary-blue;
  border-radius: 10px 10px 0 0;

  & > .menu-top-bar {
    display: flex;
    width: 100%;
    height: 64px;
    align-items: center;
    background-image: linear-gradient(
      to bottom,
      $primary-blue 30%,
      $primary-light-blue 70%
    );
    border-radius: 10px 10px 0 0;
    border-bottom: 2px solid darken($color: $primary-blue, $amount: 2%);

    & > .profile-img {
      height: 56px;
      width: 56px;
      background-image: url("../assets/img/w-logo.png");
      background-size: cover;
      background-color: $not-quite-white;
      border: 2px solid darken($color: $primary-blue, $amount: 6);
      border-radius: 8px;
      margin-left: 8px;
    }

    & > .text {
      font-size: 1.3rem;
      font-weight: bold;
      margin-left: 5px;
    }
  }
}
</style>
