<template>
  <div :class="['card', `card__${cardType}`]">
    <div class="card__content">
      <template v-if="isStockCard">
        <div class="card__img">
          <img :src="getImgUrl(imageUrl)" :alt="title" />
        </div>
        <div
          class="card__price"
          :style="`visibility: ${!amount && !description ? 'hidden' : ''}`"
        >
          <span class="card__amount">{{ amount }}</span>
          <span class="card__descr">{{ description }}</span>
        </div>
      </template>
      <h3 class="card__title">{{ title }}</h3>
      <p class="card__text">{{ text }}</p>
      <div v-if="isStockCard && estimate" class="card__estimate">
        <span class="card__deadlines">Сроки проведения акции</span>
        <span class="card__date">до {{ estimate }}</span>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";

const props = defineProps({
  isStockCard: {
    type: Boolean,
    default: false,
  },
  title: String,
  text: String,
  imageUrl: String,
  amount: String,
  description: String,
  estimate: String,
});

const cardType = ref(props.isStockCard ? "stock" : "services");
// const isNotDate = ref(isNaN(parseInt(props.estimate)));

function getImgUrl(img) {
  return "src/assets/stocks/" + img;
}
</script>
<style lang="sass" scoped>
.card
  position: relative
  max-height: 546px
  outline: 4px solid $red
  border-radius: 20px
  overflow: hidden
  transition: all .3s ease-in-out
  cursor: pointer
  &::before
    content: ''
    position: absolute
    top: 0
    right: 0
    bottom: 0
    left: 0
    transition: all .3s ease
    background: linear-gradient(3.33deg, #DE383D 2.15%, #DE6E3F 70.29%)
    opacity: 0
  &:hover
    color: $white
    outline: none
    .card__price
      background: $white
      color: $red
    .card__date
      color: $white
  &:hover::before
    opacity: 1

  &__services
    padding: 30px
    &:hover
      box-shadow: 0px 100px 80px rgba(235, 37, 20, 0.2)
    .card__title
      margin-bottom: 150px

  &__stock
    padding: 20px 20px 30px
    height: 546px

  &__content
    display: flex
    flex-direction: column
    gap: 10px
    height: 100%
    position: relative
    z-index: 1

  &__img
    max-width: 313px
    max-height: 235px
    border-radius: 10px
    overflow: hidden
    img
      width: 100%
      object-fit: cover

  &__title
    font-size: 32px
    line-height: 32px
    text-align: left

  &__text
    font-size: 24px
    line-height: 29px
    font-family: 'Open Sans', sans-serif

  &__price
    padding: 10px 14px
    display: flex
    align-items: center
    gap: 10px
    width: fit-content
    height: 58px
    color: $white
    background: $red
    border-radius: 10px
    transition: all .3s ease-in-out

  &__amount
    font-family: 'Lora', serif
    font-size: 32px
    line-height: 100%
    white-space: nowrap

  &__descr
    font-family: 'Open Sans', sans-serif
    font-size: 16px
    line-height: 120%
    text-align: left

  &__estimate
    display: flex
    flex-direction: column
    align-items: flex-start
    position: absolute
    bottom: 0
    left: 0
    font-family: 'Open Sans', sans-serif

  &__deadlines, &__date
    display: block

  &__date
    color: $red
    transition: all .3s ease-in-out

@media screen and (max-width: 1023px)
  .card
    &__services
      .card__title
        margin-bottom: 50px

    &__title
      font-size: 26px
      line-height: 26px

    &__text
      font-size: 20px
      line-height: 24px

@media screen and (max-width: 888px)
  .card
    outline: 2px solid $red
    &__services
      padding: 15px

    &__title
      font-size: 4vw
      line-height: 4vw

    &__text
      font-size: 14px
      line-height: 18px
</style>
