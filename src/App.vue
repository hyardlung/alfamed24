<template>
  <v-header />
  <router-view />
  <v-footer />
</template>

<script setup>
// import ref from "vue";
import VHeader from "./components/VHeader.vue";
import VFooter from "./components/VFooter.vue";

// const name = ref("App");
// export default {
//   components: {VHeader},
//   data() {
//     return {
//       name: 'App',
//     };
//   },
// };
</script>

<style lang="sass">
// @import url('https://fonts.googleapis.com/css2?family=Lora:wght@500&display=swap')
// @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400&display=swap')

.title
  &_large
    font-size: 56px
    line-height: 56px
    @media screen and (max-width: 767px)
      font-size: 44px
      line-height: 44px
    @media screen and (max-width: 380px)
      font-size: clamp(1.875rem, -2.7917rem + 23.3333vw, 2.75rem)
      line-height: clamp(1.875rem, -2.7917rem + 23.3333vw, 2.75rem)

  &_small
    font-size: 48px
    line-height: 48px
    @media screen and (max-width: 767px)
      font-size: 6.6vw
      line-height: 8.8vw
      @media screen and (max-width: 380px)
        font-size: 24px
        line-height: 29px

.carousel__item
  min-height: 200px
  width: 100%
  background-color: var(--vc-clr-primary)
  color: var(--vc-clr-white)
  font-size: 20px
  border-radius: 8px
  display: flex
  justify-content: center
  align-items: center

.carousel__slide
  align-items: start !important
  padding: 10px 15px

.carousel__prev,
.carousel__next
  top: -78px !important
  box-sizing: content-box
  border: 5px solid white
  width: 45px !important
  height: 45px !important
  img
    width: 100%

.carousel__prev
  right: 56px
  left: auto !important

.carousel__pagination
  align-items: center

button.carousel__pagination-button
  &::after
    width: 20px
    height: 20px
    border-radius: 50%
    background: $red
    opacity: .5
    transition: all .2s ease-in-out
  &:hover::after
    background: $red
    opacity: .7
    box-shadow: 0px 0px 8px rgba(235, 37, 20, 1)

button.carousel__pagination-button.carousel__pagination-button--active
  &::after
    width: 25px
    height: 25px
    opacity: 1
</style>
