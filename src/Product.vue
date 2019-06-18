<template>
  <div>
    <div class="product">
      <div class="product-image">
        <img :src="image" :alt="altText">
      </div>
      <div class="product-info">
        <h1>{{title}}</h1>
        <p>Shipping: {{shipping}}</p>

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

        <ProductDetailSize :sizes="sizes"/>

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
        >Add to cart</button>

        <button @click="removeFromCart">Remove from cart</button>
      </div>
    </div>
    <productReviewTabs :reviews="reviews"/>
  </div>
</template>

<script>
import ProductDetailSize from "./ProductDetailSize.vue";
import productReviewTabs from "./components/product-tabs.vue";
import eventBus from "./eventBus";

export default {
  props: {
    premium: {
      type: Boolean,
      required: true
    }
  },
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
      description: "A pair of warm, fuzzy socks",
      altText: "A pair of socks",
      link:
        "https://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=socks",
      inventory: 1,
      onSale: false,
      sizes: ["S", "M", "L", "XL", "XXL", "XXXL"],
      reviews: [
        {
          name: "name",
          review: "review",
          rating: 1
        }
      ]
    };
  },
  methods: {
    addToCart() {
      this.$emit("add-to-cart", this.variants[this.selectedVariant].variantId);
    },
    removeFromCart() {
      this.cart -= 1;
    },
    updateProduct(index) {
      // this.image = location;
      this.selectedVariant = index;
    }
  },
  computed: {
    title() {
      return `${this.brand} ${this.product}`;
    },
    image() {
      return this.variants[this.selectedVariant].variantImage;
    },
    inStock() {
      return this.variants[this.selectedVariant].variantQuantity;
    },
    shipping() {
      return this.premium ? "Free Shipping" : "2.99";
    }
  },
  components: {
    ProductDetailSize,
    productReviewTabs
  },
  mounted() {
    eventBus.$on("review-submitted", productReview => {
      this.reviews.push(productReview);
    });
  }
};
</script>

<style scoped>
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
  width: 150px;
  font-size: 14px;
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
