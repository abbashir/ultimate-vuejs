<template>
  <h1>Cart</h1>
  <ol class="list-group list-group-numbered">
    <span>
      <li class="list-group-item bg-success text-white" aria-current="true">
        Item
        <span style="float: right">Price</span>
      </li>
    </span>

    <li
      class="list-group-item d-flex justify-content-between align-items-start"
      v-for="item in items"
      :key="item.id"
    >
      <div class="ms-2 me-auto">
        {{ item.product_name }}
      </div>
      <span class="badge bg-primary rounded-pill">{{ item.price }}</span>
      <button type="button" class="btn btn-danger" @click="itemRemove(item)">
        Remove
      </button>
    </li>
    <span>
      <li class="list-group-item active" aria-current="true">
        Total:
        <span style="float: right">{{ totalPrice }}</span>
      </li>
    </span>
  </ol>
</template>

<script>
export default {
  data() {
    return {};
  },
  computed: {
    items() {
      return this.$store.getters.getCart;
    },
    totalPrice() {
      var total = 0;
      this.items.forEach((item) => {
        total += parseFloat(item.price);
      });
      return total;
    },
  },
  methods: {
    itemRemove(item) {
      this.$store.commit('removeItem', item)
    },
  },
};
</script>

<style>
</style>