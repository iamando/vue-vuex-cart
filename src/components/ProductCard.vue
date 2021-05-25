<template>
  <div
    @click="$emit('view-product', product)"
    class="flex flex-col justify-between w-72 sm:w-96 h-96 bg-white bg-center text-gray-800 shadow-md overflow-hidden cursor-pointer mx-2 my-2"
    v-bind:style="{ 'background-image': 'url(' + product.imageUrl + ')' }"
  >
    <div class="flex justify-between items-center ml-4 pr-8 mt-2">
      <div
        class="bg-indigo-600 text-white bg-opacity-95 shadow px-2 py-1 flex items-center font-bold text-xs rounded"
      >
        {{ product.brand }}
      </div>
    </div>
    <div
      class="bg-white bg-opacity-95 shadow-md rounded-r-xl p-4 flex flex-col mr-4 mb-8"
    >
      <h3 class="text-xl font-bold pb-2">{{ product.name }}</h3>
      <p class="truncate text-gray-500 text-sm">
        {{ product.description }}
      </p>
      <Ratings :ratings="product.ratings" />
      <div class="flex justify-between items-center">
        <span class="text-indigo-600 text-4xl font-bold">
          ${{ product.price.toFixed(2) }}</span
        >
      </div>
    </div>
  </div>
</template>

<script>
import Ratings from "../components/Ratings";
export default {
  props: ["product"],
  components: {
    Ratings,
  },
};
</script>
