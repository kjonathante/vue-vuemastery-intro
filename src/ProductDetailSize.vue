<template>
  <ul>
    <li v-for="(size,index) in sizes" :key="index">{{size}}</li>
  </ul>
</template>

<script>
export default {
  props: {
    sizes : {
      type: Array,
      required: true
    }
  }
}
</script>
