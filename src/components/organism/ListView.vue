<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <img
    class="
      w-64
      logo
      mt-6
      border-solid border-4 border-black
      relative
      top-8
      bg-red-300
      shadow-xl
    "
    src="../../assets/simpsonslogo.svg"
  />
  <h1 v-if="loading" class="flex justify-center">Loading...</h1>
  <div v-else>
    <div
      class="
        flex
        justify-end
        container-buttons
        margin-o-auto
        lg:m-16
        md:m-4
        max-w-screen-2xl
      "
    >
      <SortButton
        @up="sortCharacters('up')"
        :activeSort="activeSortASC"
        direction="up"
        text="Sort ascending"
      />
      <SortButton
        @down="sortCharacters('down')"
        :activeSort="activeSortDESC"
        direction="down"
        text="Sort descending"
      />
    </div>
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
    <div
      class="
        container-buttons
        flex
        mobile:flex-row
        flex-col
        justify-center
        max-w-screen-2xl
      "
    >
      <LoadButton
        @click="fetchData(5)"
        text="5 Quotes are good"
        class="inline-block"
      />
      <LoadButton
        @click="fetchData(10)"
        text="10 Quotes are better"
        class="inline-block"
      />
      <LoadButton
        @click="fetchData(15)"
        text="15 Quotes are the best"
        class="inline-block"
      />
    </div>
  </div>
</template>

<script>
import { ref, onMounted, nextTick, computed, onUpdated, watch } from "vue";
import axios from "axios";
import SortButton from "../atomic/SortButton.vue";
import LoadButton from "../atomic/LoadButton.vue";

export default {
  name: "ListView",
  components: { LoadButton, SortButton },
  setup() {
    const charactersFromLocalStorage = ref(null);
    const simpsonCharacters = ref([]);
    const loading = ref(true);
    const activeSortASC = ref(false);
    const activeSortDESC = ref(false);

    // Fetch data.
    const fetchData = async (numOfCharacters) => {
      await axios
        .get(
          `https://thesimpsonsquoteapi.glitch.me/quotes?count=${numOfCharacters}`
        )
        .then((response) => {
          simpsonCharacters.value = [...response.data];
        })
        .then(() => {
          //Set data to local storage.
          localStorage.setItem(
            "simpsonCharacters",
            JSON.stringify(simpsonCharacters.value)
          );
        })
        .catch((error) => {
          console.log("error", error);
        })
        .finally(() => (loading.value = false));
    };

    // Sort characters based on the name.
    const sortCharacters = (direction) => {
      if (direction === "up" && activeSortASC.value === false) {
        activeSortASC.value = true;
        activeSortDESC.value = false;
        return simpsonCharacters.value.sort((a, b) =>
          a.character.localeCompare(b.character)
        );
      }
      if (direction === "down" && activeSortDESC.value === false) {
        activeSortDESC.value = true;
        activeSortASC.value = false;
        return simpsonCharacters.value.sort((a, b) =>
          b.character.localeCompare(a.character)
        );
      } else {
        return simpsonCharacters;
      }
    };

    onMounted(async () => {
      if (charactersFromLocalStorage.value === null) {
        await fetchData(10);
      } else {
        loading.value = false;
      }
    });

    watch(async () => {
      //Get data from local storage.
      charactersFromLocalStorage.value = JSON.parse(
        localStorage.getItem("simpsonCharacters")
      );
      //Add new data and previous data from local storage.
      simpsonCharacters.value = [
        ...simpsonCharacters.value,
        ...charactersFromLocalStorage.value,
      ];
    });

    return {
      simpsonCharacters,
      fetchData,
      loading,
      sortCharacters,
      activeSortASC,
      activeSortDESC,
    };
  },
};
</script>

<style scoped lang="css">
.margin-o-auto {
  margin: 0 auto;
}

.logo {
  margin: 1rem auto 4rem auto;
}
</style>
