<template>
  <div class="window selected" :style="styles">
    <WindowBar title="Random Window" @mousedown="onMouseDown" />
    <div class="white-box"></div>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent, onMounted, onUnmounted, reactive, ref } from "@vue/runtime-core";
import WindowBar from "./WindowBar.vue";

export default defineComponent({
  components: {
    WindowBar,
  },
  props: {
    width: {
      default: "500px",
      type: String,
    },
    height: {
      default: "250px",
      type: String,
    },
    x: {
      default: 300,
      type: Number,
    },
    y: {
      default: 200,
      type: Number,
    },
  },
  setup: (props) => {
    const isGrabbed = ref(false);

    const pos = reactive({ x: props.x, y: props.y });

    const styles = computed((): Record<string, string> => {
      let _styles: Record<string, string> = {
        width: props.width,
        height: props.height,
        top: pos.x + "px",
        left: pos.y + "px",
      };

      return _styles;
    });

    const onMouseDown = (evt: MouseEvent) => {
      if (evt.button === 0) {
        isGrabbed.value = !isGrabbed.value;
      }
    };

    const onMouseMove = (evt: MouseEvent) => {
      if (evt.button === 0 && isGrabbed.value) {
        pos.x = evt.clientY;
        pos.y = evt.clientX;
      }
    };

    const onMouseUp = (evt: MouseEvent) => {
      if (evt.button === 0) {
        isGrabbed.value = false;
      }
    };

    onMounted(() => {
      window.addEventListener("mousemove", onMouseMove, { passive: true });
      window.addEventListener("mouseup", onMouseUp, { passive: true });
    })

    onUnmounted(() => {
      window.removeEventListener("mousemove", onMouseMove);
      window.removeEventListener("mouseup", onMouseUp);
    })

    return { styles, onMouseDown };
  },
});
</script>

<style lang="scss">
@import "~@/assets/scss/_variables.scss";

.selected {
  box-shadow: 0 0 0 1px $selected;
}

.window {
  position: fixed;
  border: 4px solid $primary-blue;
  border-radius: 8px 8px 0px 0px;
  background-color: $not-quite-white;
  // Edit at run time
}
.white-box {
  width: 50px;
  height: 50px;
  background-color: #fff;
}
</style>
