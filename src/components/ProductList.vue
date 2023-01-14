<template>
  <div class="product-list">
    <transition-group name="product-card-animation">
    <product-card
        v-for="productCard in productList"
        v-bind:productCard="productCard"
        :key="productCard.id"
        @remove="$emit('remove', productCard)"/>
    </transition-group>
  </div>
</template>

<script>
import ProductCard from "@/components/ProductCard";

export default {
  name: "product-list",
  props: {
    productList:{
      type: Array,
      required: true,
    }
  },
  components: {ProductCard},
}
</script>

<style lang="scss" scoped>

.product-list {
  max-width: 1028px;
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
}

.product-card-animation-item {
  display: inline-block;
  margin-right: 10px;
}
.product-card-animation-enter-active,
.product-card-animation-leave-active {
  transition: all 0.6s ease;
}
.product-card-animation-enter,
.product-card-animation-leave-to {
  opacity: 0;
  transform: translateX(130px);
}
.product-card-animation-move {
  transition: transform 0.8s ease;
}

</style>
