<template>
  <div class="product">
    <div class="product-image">
      <img :src="image" :alt="altText">
    </div>
    <div class="product-info">
      <h1>{{product}}</h1>
      <p>{{description}}</p>
      <a :href="link" target="_blank">More products like this</a>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      product: "socks",
      description: "A pair of warm, fuzzy socks",
      image: "./src/vmSocks-green-onWhite.jpg",
      altText: "A pair of socks",
      link:
        "https://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=socks"
    };
  }
};
</script>
<style>
img {
  border: 1px solid #d8d8d8;
  width: 70%;
  margin: 40px;
  box-shadow: 0px 0.5px 1px #d8d8d8;
}
.product {
  display: flex;
  flex-flow: wrap;
  padding: 1rem;
}
.product-image,
.product-info {
  margin-top: 10px;
  width: 50%;
}
</style>
