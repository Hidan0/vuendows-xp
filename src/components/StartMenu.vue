<template>
  <div class="menu-window">
    <div class="menu-top-bar">
      <div class="profile-img" :style="bgImg"></div>
      <span class="text">Jeff B.</span>
    </div>
    <div class="menu-body">
      <div class="mb-left"></div>
      <div class="mb-right"></div>
    </div>
    <div class="menu-bottom-bar">
      <div class="mbb-btn">
        <div class="log-off"></div>
        <span class="text">Log Off</span>
      </div>
      <div class="mbb-btn">
        <div class="turn-off"></div>
        <span class="text">Turn Off Computer</span>
      </div>
    </div>
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

  & > .menu-body {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-areas: "left right";
    box-sizing: border-box;
    width: 100%;
    height: 506px; // 620 - 64 - 2 (border) - 48
    border-right: 3px solid darken($color: $primary-blue, $amount: 1%);
    border-bottom: 2px solid darken($color: $primary-blue, $amount: 1%);

    & > .mb-left {
      grid-area: "left";
      height: 100%;
    }

    & > .mb-right {
      grid-area: "right";
      height: 100%;
      background: $light-blue;
      border-left: 2px solid darken($color: $light-blue, $amount: 10%);
    }
  }

  & > .menu-bottom-bar {
    display: flex;
    width: 100%;
    height: 48px;
    background-image: linear-gradient(
      to bottom,
      $primary-light-blue 10%,
      $primary-blue 90%
    );
    align-items: center;
    justify-content: flex-end;

    & > .mbb-btn {
      // menu-bottom-bar-btn
      display: flex;
      align-items: center;
      width: max-content;
      height: 30px;
      margin-left: 20px;
      margin-right: 30px;

      &:hover {
        cursor: pointer;
        font-size: 1.05rem;
        color: #fff;
      }

      & > .log-off {
        width: 30px;
        height: 30px;
        background-image: url("../assets/img/log-off.png");
        background-size: cover;
        box-sizing: border-box;
        border: 2px solid $not-quite-white;
        border-radius: 4px;
        margin-right: 10px;
      }

      & > .turn-off {
        width: 30px;
        height: 30px;
        background-image: linear-gradient(
          -30deg,
          $danger 60%,
          lighten($color: $danger, $amount: 25%)
        );
        box-sizing: border-box;
        border: 2px solid $not-quite-white;
        border-radius: 4px;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-right: 10px;

        &::before {
          position: absolute;
          content: "";
          width: 14px;
          height: 14px;
          border: 2px solid $not-quite-white;
          border-radius: 50%;
        }

        &::after {
          content: "";
          width: 2px;
          height: 9px;
          position: relative;
          background: $not-quite-white;
        }
      }
    }
  }
}
</style>
