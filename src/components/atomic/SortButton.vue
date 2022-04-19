<template>
  <div>
    <button
      @click="$emit(directionSort)"
      class="
        inline-block
        mr-6
        bg-green-500
        text-white
        font-bold
        py-2
        px-4
        rounded
        border-solid border-4 border-black
        shadow-xl
      "
      :class="{
        'bg-green-700': active,
      }"
    >
      {{ buttonText }}
    </button>
  </div>
</template>
<script>
// make the button work, so that it will sort according to the `direction` prop
import { computed } from "vue";
export default {
  name: "SortButton",
  props: {
    text: String,
    direction: String,
    activeSort: Boolean,
  },

  setup(props) {
    const active = computed(() => props?.activeSort);
    const buttonText = props.text;
    const directionSort = props.direction;

    return {
      active,
      buttonText,
      directionSort,
    };
  },
};
</script>
