<template>
  <div class="window" :style="styles">
    <WindowBar title="Random Window" @mousedown="onMouseDown" />
    <slot></slot>
  </div>
  <div class="border-sel" :style="h_styles"></div>
</template>

<script lang="ts">
import {
  computed,
  defineComponent,
  onMounted,
  onUnmounted,
  reactive,
  ref,
} from "@vue/runtime-core";
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

    const isHidden = ref(true);
    const h_pos = reactive({ x: props.x, y: props.y });
    const h_styles = computed((): Record<string, string> => {
      return {
        display: isHidden.value ? "none" : "",
        width: props.width,
        height: props.height,
        top: h_pos.x + "px",
        left: h_pos.y + "px",
      };
    });

    const onMouseDown = (evt: MouseEvent) => {
      if (evt.button === 0) {
        isGrabbed.value = !isGrabbed.value;
        isHidden.value = false;
      }
    };

    const onMouseMove = (evt: MouseEvent) => {
      if (evt.button === 0 && isGrabbed.value) {
        h_pos.x = evt.clientY;
        h_pos.y = evt.clientX;
      }
    };

    const onMouseUp = (evt: MouseEvent) => {
      if (evt.button === 0) {
        if (isGrabbed.value) {
          pos.y = evt.clientX;
          pos.x = evt.clientY;
        }
        isGrabbed.value = false;
        isHidden.value = true;
      }
    };

    onMounted(() => {
      window.addEventListener("mousemove", onMouseMove, { passive: true });
      window.addEventListener("mouseup", onMouseUp, { passive: true });
    });

    onUnmounted(() => {
      window.removeEventListener("mousemove", onMouseMove);
      window.removeEventListener("mouseup", onMouseUp);
    });

    return { styles, h_styles, onMouseDown };
  },
});
</script>

<style lang="scss">
@import "~@/assets/scss/_variables.scss";

.border-sel {
  position: fixed;
  border-width: 50px;
  border: 1px dashed $selected;
  box-shadow: inset 0 0 4px 1px $selected;
  background: rgba($color: $primary_light_blue, $alpha: 0.2);
}

.window {
  position: fixed;
  border: 4px solid $primary-blue;
  border-left-color: darken($color: $primary-blue, $amount: 3%);
  border-right-color: darken($color: $primary-blue, $amount: 3%);
  border-radius: 8px 8px 0px 0px;
  background-color: $not-quite-white;
}
</style>
