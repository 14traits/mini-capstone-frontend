<script>
import axios from "axios";
export default {
  data: function () {
    return {
      products: [],
      images: [],
    };
  },
  created: function () {
    this.productIndex();
  },
  methods: {
    productIndex: function () {
      axios.get("/products.json").then((response) => {
        this.products = response.data;
        console.log("All products:", this.products);
      });
    },
  },
};
</script>

<template>
  <div v-for="product in products" v-bind:key="product.id">
    <div v-for="image in product.images" v-bind:key="image.id">
      <div class="card" style="width: 18rem">
        <img :src="image.url" alt="blah blah" />
        <div class="card-body">
          <h5 class="card-title">{{ product.name }}</h5>
          <p class="card-text">
            {{ product.prices }}
          </p>
          <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
      </div>
    </div>
  </div>
</template>
