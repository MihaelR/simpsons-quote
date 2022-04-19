<template>
  <div>
    <button
      class="
        ml-6
        mt-6
        bg-red-300
        hover:bg-red-600
        text-white
        font-bold
        py-2
        px-4
        rounded
        border-solid border-4 border-black
        shadow-xl
      "
    >
      {{ buttonText }}
    </button>
  </div>
</template>
<script>
// make the button work, so that it will sort according to the `direction` prop
export default {
  name: "LoadButton",
  props: {
    text: String,
  },

  setup(props) {
    const buttonText = props?.text;
    return {
      buttonText,
    };
  },
};
</script>
