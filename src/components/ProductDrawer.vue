<template>
  <div
    class="flex flex-wrap justify-center w-full"
    :class="[active ? 'block' : 'hidden']"
  >
    <div
      class="bg-gray-200 w-full min-w-screen min-h-screen flex items-center p-5 lg:p-10 overflow-hidden relative"
    >
      <div
        :class="[active ? 'block' : 'hidden']"
        class="w-full max-w-6xl rounded bg-white shadow-xl p-10 lg:p-20 mx-auto text-gray-800 relative md:text-left"
      >
        <div class="cursor-pointer flex justify-end">
          <button
            @click="$emit('close-product-drawer')"
            class="bg-red-600 px-6 py-2 rounded text-white hover:bg-red-700"
          >
            <i class="fas fa-times mr-2"></i>
            Close
          </button>
        </div>
        <div class="md:flex items-center -mx-10" v-if="product">
          <div
            class="w-full md:w-1/2 px-10 mb-10 md:mb-0 flex justify-center items-center"
          >
            <div class="relative">
              <img
                v-bind:src="product.imageUrl"
                class="w-60 relative z-10 h-80 object-center"
                v-bind:alt="product.name"
              />
            </div>
          </div>
          <div class="w-full md:w-1/2 px-10">
            <div class="mb-10">
              <h1 class="font-bold uppercase text-2xl mb-5">
                {{ product.name }}
              </h1>
              <p class="text-sm">
                {{ product.description }}
                <router-link
                  to="#"
                  class="opacity-50 text-gray-900 hover:opacity-100 inline-block text-xs leading-none border-b border-gray-900"
                  >MORE <i class="mdi mdi-arrow-right"></i
                ></router-link>
              </p>
              <p v-if="productTotal" class="text-sm font-bold mt-2">
                IN CART : <span class="text-3xl ml-2">{{ productTotal }}</span>
              </p>
            </div>
            <div>
              <div class="inline-block align-bottom mr-5">
                <span class="text-2xl leading-none align-baseline">$</span>
                <span class="font-bold text-5xl leading-none align-baseline">{{
                  product.price.toFixed(2)
                }}</span>
              </div>
              <div
                class="inline-block align-bottom flex justify-between items-center mt-6"
              >
                <button
                  @click="addToCart"
                  class="flex justify-center items-center mr-2 bg-indigo-700 opacity-75 hover:opacity-100 text-white hover:text-white rounded px-10 py-2 font-semibold"
                >
                  <i class="fas fa-cart-plus"></i> ADD TO CART
                </button>
                <button
                  @click="removeFromCart"
                  class="flex justify-center items-center ml-2 bg-indigo-700 opacity-75 hover:opacity-100 text-white hover:text-white rounded px-10 py-2 font-semibold"
                >
                  <i class="fas fa-trash"></i> REMOVE FROM CART
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["product", "active"],
  computed: {
    productTotal() {
      return this.$store.getters.productQuantity(this.product);
    },
  },
  methods: {
    addToCart() {
      this.$store.commit("addToCart", this.product);
      this.$notify({
        type: "success",
        text: "You added this on your Cart",
      });
    },
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
