<template>
  <div class="card">
    <div class="card__container">
      <img src="../assets/images/card-image.png" alt="" class="card__image">
      <div class="card__content">
        <div class="card__title">Наименование товара</div>
        <div class="card__description">Довольно-таки интересное описание товара в несколько строк. Довольно-таки
          интересное описание товара в несколько строк
        </div>
        <div class="card__price">10 000 руб.</div>
      </div>
    </div>
    <div class="card__remove" @click="cardRemove">
      <img src="../assets/icons/delete-card.svg" alt="">
    </div>
  </div>
</template>

<script>
export default {
  name: "product-card",
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
   }

  &__image {
    object-fit: cover;
    width: 100%;
    height: 100%;
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
    padding: 0 0 32px 0;
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
