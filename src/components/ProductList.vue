<template>
  <div class="product-list">
    <product-card/>
    <product-card/>
    <product-card/>
    <product-card/>
    <product-card/>
    <product-card/>
    <product-card/>
  </div>

</template>

<script>
import ProductCard from "@/components/ProductCard";

export default {
  name: "product-list",
  components: {ProductCard}

}
</script>

<style lang="scss" scoped>
.product-list{
  max-width: 1028px;
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
}
</style>
