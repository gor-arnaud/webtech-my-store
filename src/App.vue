<template>
  <div id="app">
    <h1 class="title">Shaine</h1>
    <input type="text" v-model="search" placeholder="Rechercher un produit..." class="search-bar">
    <div class="product-grid">
      <div class="product" v-for="product in filteredProducts" :key="product.id">
        <h2>{{ product.title }}</h2>
        <img :src="product.thumbnail" :alt="product.title">
      </div>
    </div>
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
      search: '',
    };
  },
  computed: {
    filteredProducts() {
      return this.products.filter(product => product.title.toLowerCase().includes(this.search.toLowerCase()));
    }
  },
  mounted() {
    axios.get("https://dummyjson.com/products").then((result) => {
      this.products = result.data.products;
    });
  },
};
</script>

<style>
.search-bar {
  display: block;
  width: 100%;
  max-width: 300px;
  padding: 10px;
  margin: 20px auto;
  font-size: 1em;
  border-radius: 5px;
  border: 1px solid #ccc;
}

body {
  font-family: Arial, sans-serif;
  background-color: #f4f4f4;
  margin: 0;
  padding: 0;
}

.title {
  text-align: center;
  font-size: 2.5em;
  margin-bottom: 30px;
  color: #333;
  text-transform: uppercase;
}

.product-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  padding: 0 10px;
}

.product {
  flex: 1 0 23%;
  box-sizing: border-box;
  padding: 10px;
  margin: 10px;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

.product h2 {
  font-size: 1.5em;
  color: #333;
  margin-bottom: 20px;
}

.product img {
  width: 100%;
  height: auto;
  border-radius: 5px;
}
</style>
