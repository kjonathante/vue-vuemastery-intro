<template>
  <div>
    <h1>{{product}}</h1>
    <p>{{description}}</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      product: "socks",
      description: "A pair of warm, fuzzy socks"
    };
  }
};
</script>
