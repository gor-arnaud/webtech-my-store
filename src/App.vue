<template>
  <div id="app">
    <h1>Bdiscount</h1>

    <div class="product-list">
      <div class="product" v-for="product in products" :key="product.id">
        <h2> {{ product.title }} </h2>
        <img :src="product.thumbnail" />
        <p>{{ product.description }}</p>
        <p class="price">{{ product.price }} €</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  components: {},
  data() {
    return {
      products: []
    }
  },
  mounted() {
    axios.get('https://dummyjson.com/products')
      .then(result => {
        this.products = result.data.products;
      });
  }
}
</script>

<style>
@font-face {
  font-family: 'Outward';
  src: url('@/assets/Font/outward-master/fonts/ttf/outward-round.ttf') format('truetype');
  font-weight: normal;
  font-style: normal;
}

* {
  margin: 0;
  padding: 0;
}

h1 {
  text-align: center;
  padding-bottom: 30px;
  padding-top: 30px;
  align-items: center;
  display: flex;
  justify-content: left;
  color: white;
  font-size: 10em;
  background-color: black;
  padding-left: 110px;
  font-family: 'Outward', sans-serif;
}

.product-list {
  padding-top: 50px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  background-color: #AEAEAC;

  /* gap: 20px; */
}

.product {
  padding: 20px;
  /* padding-bottom: 20px; */
  width: 400px;
  display: flex;
  flex-direction: column;
  align-items: center;
  border-radius: 10px;
  margin: 20px;
  background-color: white;


}

p {
  justify-content: center;
  text-align: center;
  margin-bottom: 15px;
}
</style>
