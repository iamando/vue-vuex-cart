<template>
  <tr>
    <td class="hidden pb-4 md:table-cell">
      <router-link to="#">
        <img
          v-bind:src="product.imageUrl"
          class="w-20 rounded"
          alt="Thumbnail"
        />
      </router-link>
    </td>
    <td>
      <a href="#">
        <p class="mb-2 md:ml-4">{{ product.name }}</p>
        <button type="submit" class="text-gray-700 md:ml-4">
          <small @click="removeFromCart">(Remove item)</small>
        </button>
      </a>
    </td>
    <td class="justify-center md:justify-end md:flex mt-6 items-center">
      <div class="w-20 h-10">
        <div class="relative flex flex-row w-full h-8 mt-5">
          <input
            type="number"
            disabled
            v-bind:value="product.quantity"
            class="w-full font-semibold text-center text-gray-700 bg-gray-200 outline-none focus:outline-none hover:text-black focus:text-black"
          />
        </div>
      </div>
    </td>
    <td class="hidden text-right md:table-cell">
      <span class="text-sm lg:text-base font-medium">
        ${{ product.price.toFixed(2) }}</span
      >
    </td>
    <td class="text-right">
      <span class="text-sm lg:text-base font-medium">
        ${{ totalPrice.toFixed(2) }}
      </span>
    </td>
  </tr>
</template>

<script>
export default {
  props: ["product"],
  computed: {
    totalPrice() {
      return this.product.price * this.product.quantity;
    },
  },
  methods: {
    removeFromCart() {
      this.$store.commit("removeFromCart", this.product);
      this.$notify({
        type: "success",
        text: "You removed this on your Cart",
      });
    },
  },
};
</script>