<template>
  <div class="app">
    <div class="app__container">
      <div class="app__header">
        <h1 class="app__title">Добавление товара</h1>
        <my-select v-model="selectedSort" :options="sortOptions"/>
      </div>
      <div class="app__content">
        <product-form/>
        <product-list/>
      </div>
    </div>
  </div>
</template>

<script>

import ProductForm from "@/components/ProductForm";
import ProductList from "@/components/ProductList";

export default {
  name: "App",
  components: {ProductForm, ProductList},
  data() {
    return {
      selectedSort: '',
      sortOptions: [
        {value: "title", name: "По названию"},
        {value: "body", name: "По описанию"}
      ]
    }
  },
  methods: {}
}
</script>

<style lang="scss" scoped>

.app {
  padding: 32px 0 0 0;
  background: rgba(255, 254, 251, 0.8);

  &__container {
    width: 100%;
    max-width: 1440px;
    margin: 0 auto;
    padding: 0 32px;
  }

  &__header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 0 0 16px 0;
  }

  &__title {
    font-family: 'Source Sans Pro', sans-serif;
    font-weight: 600;
    font-size: 28px;
    line-height: 35px;
    color: #3F3F3F;
  }

  &__content {
    display: flex;
    justify-content: space-between;
    gap: 16px;
  }
}

</style>
