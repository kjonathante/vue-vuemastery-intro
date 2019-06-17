<template>
  <div class="product">
    <div class="product-image">
      <img :src="image" :alt="altText">
    </div>
    <div class="product-info">
      <h1>{{title}}</h1>

      <p v-if="inStock">In Stock</p>
      <p v-else :class="{outOfStock: !inStock}">Out of Stock</p>

      <p v-if="inventory > 10">In Stock</p>
      <p v-else-if="inventory > 0 && inventory <=10">Almost sold out!</p>
      <p v-else>Out of Stock</p>

      <p>{{description}}</p>
      <a :href="link" target="_blank">More products like this</a>
      <span v-show="onSale">On Sale</span>

      <ul>
        <li v-for="(detail,index) in details" :key="index">{{detail}}</li>
      </ul>

      <ul>
        <li v-for="(size,index) in sizes" :key="index">{{size}}</li>
      </ul>

      <div
        class="color-box"
        v-for="(variant, index) in variants"
        :key="variant.variantId"
        :style="{backgroundColor: variant.variantColor}"
        @mouseover="updateProduct(index)"
      ></div>

      <button 
        @click="addToCart" 
        :disabled="inventory < 1" 
        :class="{disabledButton: inventory < 1}"
      >
      Add to cart
      </button>
      
      <button @click="removeFromCart">Remove from cart</button>
      
      <div class="cart">
        <p>Cart({{cart}})</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      product: "Socks",
      brand: "Vue Mastery",
      // image: "./src/vmSocks-green-onWhite.jpg",
      selectedVariant: 0,
      // inStock: false,
      details: ["80% cotton", "20% polyester", "Gender-neutral"],
      variants: [
        {
          variantId: 2234,
          variantColor: "green",
          variantImage: "./src/vmSocks-green-onWhite.jpg",
          variantQuantity: 10
        },
        {
          variantId: 2235,
          variantColor: "blue",
          variantImage: "./src/vmSocks-blue-onWhite.jpg",
          variantQuantity: 0
        }
      ],
      cart: 0,
      description: "A pair of warm, fuzzy socks",
      altText: "A pair of socks",
      link:
        "https://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=socks",
      inventory: 1,
      onSale: false,
      sizes: ["S", "M", "L", "XL", "XXL", "XXXL"],
    };
  },
  methods: {
    addToCart() {
      this.cart += 1;
    },
    removeFromCart() {
      this.cart -= 1;
    },
    updateProduct(index) {
      // this.image = location;
      this.selectedVariant = index
    }
  },
  computed: {
    title() {
      return `${this.brand} ${this.product}`
    },
    image() {
      return this.variants[this.selectedVariant].variantImage
    },
    inStock() {
      return this.variants[this.selectedVariant].variantQuantity
    }
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
button {
  margin-top: 30px;
  border: none;
  background-color: #1e95ea;
  color: white;
  height: 40px;
  width: 100px;
  font-size: 14px;
}
.cart {
  margin-right: 25px;
  float: right;
  border: 1px solid #d8d8d8;
  padding: 5px 20px;
}
.color-box {
  width: 40px;
  height: 40px;
  margin-top: 5px;
}
.disabledButton {
  background-color: #d8d8d8;
}
.outOfStock {
  color: red;
}
</style>
