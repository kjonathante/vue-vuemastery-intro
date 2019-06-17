<template>
  <div id="app">
    <div class="cart">
      <p>Cart({{cart.length}})</p>
    </div>
    <product :premium="premium" @add-to-cart="updateCart"/>
  </div>
</template>


<script>
import product from "./Product.vue";

export default {
  data() {
    return {
      premium: false,
      cart: [],
    };
  },
  methods: {
    updateCart(index) {
      // this.cart[this.cart.length] = index; // this won't work
      this.cart.push( index )
    }
  },
  components: { product }
};
</script>

<style>
#app {
  font-size: 18px;
  font-family: "Roboto", sans-serif;
  color: blue;
}
</style>