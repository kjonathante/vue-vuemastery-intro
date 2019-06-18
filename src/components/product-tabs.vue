<template>
  <div>
    <span
      class="tab"
      v-for="(tab, index) in tabs"
      :key="index"
      @click="selectedTab = tab"
      :class="{ activeTab: selectedTab === tab }"
    >{{ tab }}</span>
    <productReviews v-show="selectedTab==='Reviews'" :reviews="reviews"/>
    <productReviewForm v-show="selectedTab==='Make a Review'" />
  </div>
</template>

<script>
import productReviewForm from "./product-review-form.vue";
import productReviews from "./product-reviews.vue";
export default {
  props: {
    reviews: {
      type: Array,
      required: true,
    }
  },
  data() {
    return {
      tabs: ["Reviews", "Make a Review"],
      selectedTab: "Reviews"
    };
  },
  components: {
    productReviewForm,
    productReviews
  }
};
</script>

<style scoped>
.tab {
  margin-left: 20px;
  cursor: pointer;
}

.activeTab {
  color: #16c0b0;
  text-decoration: underline;
}
</style>
