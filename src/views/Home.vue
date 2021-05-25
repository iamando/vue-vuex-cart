<template>
  <div>
    <ProductDrawer
      :product="product"
      :active="active.product_drawer"
      v-on:close-product-drawer="closeProductDrawer"
    />
    <div class="container mx-auto">
      <div class="flex flex-wrap justify-center mt-6">
        <ProductCard
          v-for="product in products"
          :key="product.id"
          :product="product"
          v-on:view-product="viewProduct($event)"
        />
      </div>
    </div>
  </div>
</template>

<script>
import products from "../data/products";
import ProductCard from "../components/ProductCard";
import ProductDrawer from "../components/ProductDrawer";

export default {
  name: "Home",
  components: {
    ProductCard,
    ProductDrawer,
  },
  data() {
    return {
      products,
      product: null,
      active: {
        product_drawer: false,
      },
    };
  },
  methods: {
    viewProduct(product) {
      this.product = product;
      this.active.product_drawer = true;
      window.scroll(0, 0);
    },
    closeProductDrawer() {
      this.active.product_drawer = false;
    },
  },
};
</script>

