<template>
  <div class="product-form">
    <div class="product-form__container">
      <label>Наименование товара
        <input
            v-model="productCard.title"
            type="text"
            placeholder="Введите наименование товара">
      </label>
      <label>Описание товара
        <textarea
            v-model="productCard.description"
            placeholder="Введите описание товара">
        </textarea>
      </label>
      <label>Ссылка на изображение товара
        <input
            v-model="productCard.image"
            type="text"
            placeholder="Введите ссылку">
      </label>
      <label>Цена товара
        <input
            v-model="productCard.price"
            type="text"
            placeholder="Введите цену">
      </label>
      <button class="product-form__button"
              disabled="disabled"
              @click="addCard">Добавить товар
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "product-form",
  data() {
    return {
      productCard: {
        id: "",
        title: "",
        description: "",
        image: "",
        price: "",
      }
    }
  },
  methods: {
    addCard() {
      this.productCard.id = Date.now()
      this.$emit('addCard', this.productCard)
      this.productCard = {
        title: "",
        description: "",
        image: "",
        price: "",
      }
    },
  }
}
</script>

<style lang="scss" scoped>

label {
  display: flex;
  flex-direction: column;
  font-weight: 400;
  font-size: 10px;
  line-height: 13px;
  letter-spacing: -0.02em;
  color: #49485E;
  padding: 0 0 16px 0;
}

.product-form {
  min-width: 332px;
  height: 100%;
  background: #FFFEFB;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  padding: 24px;
}

input {
  margin-top: 4px;
  outline: none;
  padding: 10px 0 10px 16px;
  font-family: 'Source Sans Pro', sans-serif;
  font-weight: 400;
  font-size: 12px;
  line-height: 15px;
  color: #3F3F3F;
  background: #FFFEFB;
  border: none;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
}

textarea {
  resize: none;
  min-height: 108px;
  margin-top: 4px;
  font-family: 'Source Sans Pro', sans-serif;
  outline: none;
  font-weight: 400;
  font-size: 12px;
  line-height: 15px;
  color: #3F3F3F;
  padding: 10px 0 0 16px;
  background: #FFFEFB;
  border-radius: 4px;
  border: none;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
}

.product-form__button {
  width: 100%;
  padding: 10px 0 10px 0;
  background: #EEEEEE;
  border-radius: 10px;
  border: none;
  font-family: 'Source Sans Pro', sans-serif;
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  letter-spacing: -0.02em;
  color: #B4B4B4;
  cursor: pointer;
}

.product-form__button:hover {
  background: #000;
  color: white;
}

input::-webkit-input-placeholder {
  color: #B4B4B4;
}

textarea::-webkit-input-placeholder {
  color: #B4B4B4;
}
</style>
