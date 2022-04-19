<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <div
    class="container-characters margin-o-auto lg:m-16 md:m-4 max-w-screen-2xl"
  >
    <div
      v-for="quote in simpsonCharacters"
      :key="quote"
      class="inline-block desktop:w-1/5 mobile:w-1/3 w-full h-96"
    >
      <div
        class="
          desktop:pt-8 desktop:p-4
          flex-1 flex flex-col
          justify-between
          p-8
          bg-gradient-to-br
          border-solid border-4 border-yellow-300
          duration-300
          from-cyan-100
          hover:scale-110
          rounded-lg
          shadow-xl
          h-[21rem]
          m-6
        "
      >
        <div class="desktop:flex">
          <img
            class="
              desktop:w-16
              w-32
              h-32
              flex-shrink-0
              mx-auto
              rounded-full
              shadow-xl
              bg-white
              border-4 border-black
            "
            :src="quote.image"
            alt="image of quote.character"
          />
          <h3
            class="
              desktop:ml-4 desktop:mt-0
              mt-6
              text-gray-900 text-center text-xs
              h-28
              overflow-x-auto
              justify-center
              flex
            "
          >
            {{ quote.quote }}
          </h3>
        </div>
        <h2 class="text-gray-900 font-bold text-center text-s">
          {{ quote.character }}
        </h2>
      </div>
    </div>
  </div>
</template>

<script>
import SortButton from "../atomic/SortButton.vue";
import LoadButton from "../atomic/LoadButton.vue";
import { ref } from "vue";

export default {
  name: "ListOfCharacter",

  components: { LoadButton, SortButton },

  props: {
    simpsonCharacters: ref,
  },

  setup(props) {
    const simpsonCharacters = computed(() => props?.activeSort);

    return {
      simpsonCharacters,
    };
  },
};
</script>

<style scoped lang="css">
.margin-o-auto {
  margin: 0 auto;
}
</style>
