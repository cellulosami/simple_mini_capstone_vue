/* eslint-disable prettier/prettier */

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="product in products" v-bind:key="product.id">
      {{ product.name }}
      <div>
        <img v-bind:src="product.image_url">
      </div>
      <hr>
      </div>
  </div>
</template>

<style>
img {
  width: 250px;
}
</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      products: [],
    };
  },
  created: function () {
    console.log("hello");
    this.indexProducts();
  },
  methods: {
    indexProducts: function () {
      console.log("hello from indexProducts");
      axios.get("http://localhost:3000/api/products").then((response) => {
        console.log(response);
        this.products = response.data;
      });
    },
  },
};
</script>
