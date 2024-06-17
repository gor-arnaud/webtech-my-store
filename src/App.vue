<template>
  <div id="app">
    <span
      >{{ products.length }} produits à votre disposition pour construire votre
      site e-commerce</span
    >
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  components: {},
  data() {
    return {
      products: [],
    };
  },
  mounted() {
    axios.get("https://dummyjson.com/products").then((result) => {
      this.products = result.data.products;
    });
  },
};
</script>

<style></style>
