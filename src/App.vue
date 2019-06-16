<template>
  <div id="app">
    {{ message }}
    <Product />
  </div>
</template>


<script>
import Product from "./Product.vue"

export default {
  data() {
    return {
      message: "Hello World"
    };
  },
  components: { Product }
};
</script>

<style>
#app {
  font-size: 18px;
  font-family: "Roboto", sans-serif;
  color: blue;
}
</style>