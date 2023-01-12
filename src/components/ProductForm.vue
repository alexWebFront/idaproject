<template>
  <div class="product-form">
    <div class="product-form__container">
      <label>Наименование товара
        <input required type="text">
      </label>
      <label>Описание товара
        <textarea></textarea>
      </label>
      <label>Ссылка на изображение товара
        <input required type="text">
      </label>
      <label>Цена товара
        <input required type="text">
      </label>
      <button type="submit" @click="addCard">Добавить товар</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "product-form",
  data() {
    return {
      name: "",
      description: "",
      image: "",
      price: "",
      productList: [
        {name: "Название", description: "Описание", image: "Картинка", price: "Цена"}
      ]
    }
  },
  methods: {
    addCard() {
      console.log(this.productList);
    }
  }
}
</script>

<style lang="scss" scoped>

label {
  display: flex;
  flex-direction: column;
}

.product-form {
  max-width: 332px;
  height: 440px;
  border: 1px solid black;
  background: #FFFEFB;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  padding: 24px;
}

textarea {
  resize: none;
}
</style>
