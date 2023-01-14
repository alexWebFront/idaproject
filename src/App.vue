<template>
  <div class="app">
    <div class="app__container">
      <div class="app__header">
        <h1 class="app__title">Добавление товара</h1>
        <my-select
            v-model="selectedSort"
            :options="sortOptions"/>
      </div>
      <div class="app__content">
        <product-form @addCard="addCard"/>
        <product-list
            :productList="sortedList"
            @remove="removeCard"/>
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
        {value: "min", name: "По цене min"},
        {value: "max", name: "По цене max"},
        {value: "title", name: "По наименованию"},
      ],
      productList: [
        {
          id: 1,
          title: "Наименование товара4",
          description: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          image: require('./assets/images/card-image.png'),
          price: "40000",
        },
        {
          id: 2,
          title: "Наименование товара2",
          description: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          image: require('./assets/images/card-image.png'),
          price: "20000",
        },
        {
          id: 3,
          title: "Наименование товара5",
          description: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          image: require('./assets/images/card-image.png'),
          price: "12000",
        },
        {
          id: 4,
          title: "Наименование товара1",
          description: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          image: require('./assets/images/card-image.png'),
          price: "12",
        },
        {
          id: 5,
          title: "Наименование товара8",
          description: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          image: require('./assets/images/card-image.png'),
          price: "10",
        },
      ],
    }
  },
  methods: {
    addCard(productCard) {
      this.productList.push(productCard);
      this.setLocalStorage();
    },

    removeCard(productCard) {
      this.productList = this.productList.filter(card => card.id !== productCard.id);
      this.setLocalStorage();
    },

    setLocalStorage() {
      localStorage.setItem("productCard", JSON.stringify(this.productList));
    },

    setList() {
      const addLocalStorageList = JSON.parse(localStorage.getItem("productCard"))
      this.productList = addLocalStorageList
          ? addLocalStorageList
          : this.productList;
    },
  },
  computed: {
    sortedList() {
      return this.productList.sort((value1, value2) => {
        if (this.selectedSort === "title") {
          return value1["title"]?.localeCompare(value2["title"]);
        }
        if (this.selectedSort === "min") {
          return value1["price"]?.localeCompare(value2["price"]);
        }
        if (this.selectedSort === "max") {
          return value2["price"]?.localeCompare(value1["price"]);
        }
        return this.productList;
      })
    }
  },
  created() {
    this.setList();
  }
}

</script>

<style lang="scss" scoped>
@import "./assets/variables";

.app {
  background-color: $background-color;

  &__container {
    width: 100%;
    max-width: 1440px;
    min-height: 900px;
    margin: 0 auto;
    padding: 32px 32px 0 32px;
    background: rgba(255, 254, 251, 0.8);
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
