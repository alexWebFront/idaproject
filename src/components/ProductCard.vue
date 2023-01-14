<template>
  <div class="card">
    <div class="card__container">
      <div class="card__image">
        <img :src="productCard.image" alt="Картинка товара">
      </div>
      <div class="card__content">
        <div class="card__title">{{ productCard.title }}</div>
        <div class="card__description">{{ productCard.description }}
        </div>
        <div class="card__price">{{ productCard.price }} руб.</div>
      </div>
    </div>
    <div class="card__remove" @click="$emit('remove', productCard)">
      <img src="../assets/icons/delete-card.svg" alt="">
    </div>
  </div>
</template>

<script>
export default {
  name: "product-card",
  props: {
    productCard: {
      type: Object,
      required: true,
    }
  },
  methods: {
    cardRemove() {
      console.log("Удалено!")
    }
  }
}
</script>

<style lang="scss" scoped>
.card {
  max-width: 332px;
  position: relative;
  cursor: pointer;

  &__container {
    background: #FFFEFB;
    box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;
  }

  &__content {
    padding: 16px 16px 24px 16px;
    min-height: 223px;
  }

  &__image {
    width: 332px;
    height: 200px;

    img {
      object-fit: cover;
      background-position: center;
      width: 100%;
      height: 100%;
    }
  }

  &__title {
    font-weight: 600;
    font-size: 20px;
    line-height: 25px;
    color: #3F3F3F;
    padding: 0 0 16px 0;
  }

  &__description {
    font-weight: 400;
    font-size: 16px;
    line-height: 20px;
    color: #3F3F3F;
    margin: 0 0 32px 0;
    height: 80px;
  }

  &__price {
    font-weight: 600;
    font-size: 24px;
    line-height: 30px;
    color: #3F3F3F;
  }

  &__remove {
    width: 32px;
    height: 32px;
    position: absolute;
    top: -8px;
    right: -8px;
    display: none;

    img {
      width: 100%;
      height: 100%;
    }
  }
}

.card:hover .card__remove {
  display: block;
}
</style>
