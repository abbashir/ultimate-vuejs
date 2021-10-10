<template>
  <div class="row">
    <div class="col-md-8">
      <div class="card">
          <img :src="product.image" class="card-img-top" alt="..." />

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
  beforeCreate() {
      axios.get("http://localhost:3000/products/" + this.$route.params.id).then((res) => {
        this.product = res.data;
      });
    },
  data() {
    return {
      product: null,
    };
  },
  mounted() {
  },
  methods: {
    addToCart(item) {
      this.$store.commit("addToCart", item);
    },
  },
};
</script>
