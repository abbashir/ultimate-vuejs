<template>
  <h1>Product list</h1>

  <div v-if="loading" class="spinner-border text-primary" role="status">
    <span class="visually-hidden">Loading...</span>
  </div>

  <div class="row">
    <div class="col-md-4" v-for="product in products" :key="product.id">
      <div class="card">
        <router-link :to="{ name: 'ItemDetails', params: { id: product.id } }">
          <img :src="product.image" class="card-img-top" alt="..." />
        </router-link>

        <div class="card-body">
          <h5 class="card-title" style="font-size: 14px">
            {{ product.product_name }}
          </h5>
          <p class="card-text">
            {{ product.details }}
          </p>
        </div>
        <div class="card-body">
          <h4 style="float: left">Price: {{ product.price }}</h4>
          <button
            type="button"
            class="btn btn-primary"
            style="float: right"
            @click="addToCart(product)"
          >
            Add to cart
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      loading: true,
      products: [],
    };
  },
  mounted() {
    var self = this;
    axios.get("http://localhost:3000/products").then((res) => {
      self.products = res.data;
      self.loading = false;
    });
  },
  methods: {
    addToCart(item) {
      this.$store.commit("addToCart", item);
    },
  },
};
</script>

<style>
</style>