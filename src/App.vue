<template>
  <Navbar />
  <notifications class="mt-14" />
  <router-view />
</template>

<script>
import Navbar from "./components/Navbar.vue";
export default {
  components: {
    Navbar,
  },
  mounted() {
    this.$store.commit("updateCartFromLocalStorage");
  },
};
</script>