<template>
  <Navbar></Navbar>
  <div class="container-fluid">
    <div class="row">
      <div class="col-8">
        <!-- dynamically view render here -->
        <router-view />
      </div>
      <div class="col-4">
        <Cart></Cart>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import Cart from "@/components/Cart.vue";
export default {
  data() {
    return {
      title: "Home",
    };
  },
  components: {
    Navbar,
    Cart,
  },
};
</script>

<style lang="scss">
a {
  color: #6bdb20;

  &.router-link-exact-active {
    color: #dd1919 !important;
  }
}
</style>
