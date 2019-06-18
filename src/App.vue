<template>
  <div id="app">
    <div class="nav-bar"></div>
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
      cart: []
    };
  },
  methods: {
    updateCart(index) {
      // this.cart[this.cart.length] = index; // this won't work
      this.cart.push(index);
    }
  },
  components: {
    product
  }
};
</script>

<style>
body {
  font-family: tahoma;
  color: #282828;
  margin: 0px;
}
</style>

<style scoped>
.cart {
  margin-right: 25px;
  float: right;
  border: 1px solid #d8d8d8;
  padding: 5px 20px;
}
.nav-bar {
  background: linear-gradient(-90deg, #84cf6a, #16c0b0);
  height: 60px;
  margin-bottom: 15px;
}
</style>
