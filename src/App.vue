<template>
  <div id="app">
    <h1>
      Zalanda
      <img class="logo" src="./assets/Logo_Zalando.svg" alt="Zalando Logo" />
    </h1>
    <section class="product-grid">
      <div class="product" v-for="product in products" :key="product.id">
        <h2 class="product-title">{{ product.title }}</h2>
        <img
          class="product-image"
          :src="product.thumbnail"
          :alt="product.title"
        />
        <p class="product-description">{{ product.description }}</p>
        <span>{{ product.price }}</span>
      </div>
    </section>
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
@import url("https://fonts.googleapis.com/css2?family=Kanit:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
body {
  font-family: sans-serif;
}
h1 {
  font-family: "Kanit", sans-serif;
  font-weight: 300;
  font-size: 40px;
  text-align: center;
  margin-bottom: 30px;
  margin-top: 30px;
  align-items: center;
  display: flex;
  justify-content: center;
}

h1 img {
  margin-left: 10px;
}

* {
  margin: 0;
  padding: 0;
}

.product-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
}

.product {
  width: 300px;
  padding: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  box-shadow: #8a2be2 0px 0px 3px;
  border-radius: 30px;
}
.product-title {
  font-size: 1.2rem;
  margin-bottom: 10px;
}

.product-image {
  width: 100%;
  height: auto;
  object-fit: contain;
  margin-bottom: 10px;
}

.product-description {
  font-size: 0.9rem;
  color: #666;
  text-align: center;
}
.logo {
  width: 50px;
  height: auto;
}
.product span {
  font-weight: 600;
  font-size: 30px;
  color: blueviolet;
}
</style>
