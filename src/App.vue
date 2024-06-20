<template>
  <div id="app">
    <span class="texte-centre">Liste de produits</span>
    <div class="liste-des-produits">
      <div class="produit" v-for="product in products" :key="product.id">
        <h3>{{ product.title }}</h3>
        <img :src=product.thumbnail alt=product.title>
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
    };
  },
  mounted() {
    axios.get("https://dummyjson.com/products").then((result) => {
      this.products = result.data.products;
    });
  },
};
</script>

<style>
body {
  background-color: #F5F5F7;
}

.texte-centre {
    display: block;
    text-align: center;
    margin: 20px 0;
    font-size: 3em;
    font-family: 'Helvetica Neue', sans-serif;
}

.liste-des-produits {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
}

.produit {
    border: 1px solid #e0e0e0;
    background-color: #fff;
    border-radius: 8px;
    padding: 20px;
    margin: 10px;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    width: 20%;
    transition: box-shadow 0.3s ease;
    font-family: Helvetica, sans-serif;
    transition: box-shadow 0.3s ease;
}

.produit:hover {
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}


</style>
