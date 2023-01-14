<template>
  <div class="product-form">
    <div class="product-form__container">
      <label>Наименование товара
        <input
            v-model="productCard.title"
            type="text"
            placeholder="Введите наименование товара"
            :class="[{isDisabledInput:isTitleError}]">
        <span
            v-if="isTitleError"
            class="product-form__error">Поле является обязательным</span>
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
            placeholder="Введите ссылку"
            :class="[{isDisabledInput:isImageError}]">
        <span
            v-if="isImageError"
            class="product-form__error">Поле является обязательным</span>
      </label>
      <label>Цена товара
        <input
            v-model="productCard.price"
            type="text"
            placeholder="Введите цену"
            :class="[{isDisabledInput:isPriceError}]">

        <span
            v-if="isPriceError"
            class="product-form__error">Поле является обязательным</span>
      </label>
      <button class="product-form__button"
              :class="[{isDisabled:isDisabled}]"
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
      isTitleError: false,
      isImageError: false,
      isPriceError: false,
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
    clearForm() {
      this.productCard = {
        title: "",
        description: "",
        image: "",
        price: "",
      }
      this.isTitleError = false;
      this.isImageError = false;
      this.isPriceError = false;
    },

    addCard() {
      if (this.isDisabled) {
        this.isTitleError = this.productCard.title === ""
        this.isImageError = this.productCard.image === ""
        this.isPriceError = this.productCard.price === ""

        return
      }

      this.productCard.id = Date.now()
      this.productCard.price = this.productCard.price.replace(" ", "").trim()
      console.log(this.productCard.price)
      this.$emit('addCard', this.productCard)
      this.clearForm()

    },
  },
  computed: {
    isDisabled() {
      return this.productCard.title.trim() === ""
          || this.productCard.image.trim() === ""
          || this.productCard.price.trim() === ""
    },
  },
  watch: {
    productCard: {
      handler: function (val, oldVal) {
        this.productCard.price = this.productCard.price.replace(/[a-zA-Zа-яА-Я]/g, "");
        this.productCard.price = this.productCard.price
            .replace(/[^0-9.]/g, "")
            .replace(/\B(?=(\d{3})+(?!\d))/g, " ");
      },
      deep: true
    }
  }
}

</script>

<style lang="scss" scoped>
.product-form__error {
  font-weight: 400;
  font-size: 8px;
  line-height: 10px;
  letter-spacing: -0.02em;
  color: #FF8484;
  padding-top: 4px;
}

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

.isDisabledInput{
  border: 1px solid #FF8484;
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
  background: #7BAE73;
  border-radius: 10px;
  border: none;
  font-family: 'Source Sans Pro', sans-serif;
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  letter-spacing: -0.02em;
  color: #FFFFFF;
  cursor: pointer;
  outline: none;
}

.isDisabled {
  color: #B4B4B4;
  background: #EEEEEE;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  cursor: default;
}

//.product-form__button:hover {
//  background: #000;
//  color: white;
//}

input::-webkit-input-placeholder {
  color: #B4B4B4;
}

textarea::-webkit-input-placeholder {
  color: #B4B4B4;
}
</style>
