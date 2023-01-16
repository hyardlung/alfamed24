<template>
  <div class="review">
    <img
      :src="getImg(image)"
      :alt="`На фото ${fullname}`"
      class="review__img"
    />
    <span class="review__fullname">{{ fullname }}</span>
    <p class="review__text">{{ text }}</p>
    <span class="review__date">{{ date }}</span>
  </div>
</template>
<script setup>
defineProps({
  image: {
    type: String,
    required: true,
  },
  fullname: {
    type: String,
    required: true,
  },
  text: {
    type: String,
    required: true,
  },
  date: {
    type: String,
    required: true,
  },
});

function getImg(img) {
  return "src/assets/reviews/" + img;
}
// export default {
//   props: {
//     image: {
//       type: String,
//       required: true,
//     },
//     fullname: {
//       type: String,
//       required: true,
//     },
//     text: {
//       type: String,
//       required: true,
//     },
//     date: {
//       type: String,
//       required: true,
//     },
//   },
// methods: {
// getImg(img) {
//   return require("@/assets/reviews/" + img);
// },
// },
// };
</script>
<style lang="sass" scoped>
.review
  display: flex
  flex-direction: column
  justify-content: start
  align-items: start
  gap: 20px
  min-height: 455px
  height: 100%
  font-family: 'Open Sans', sans-serif

  &__img
    max-width: 130px
    border: 4px solid $red
    border-radius: 20px

  &__fullname
    font-family: 'Lora', serif
    font-size: 26px
    line-height: 26px

  &__text
    margin-bottom: 10px
    font-size: 16px
    line-height: 19px
    text-align: left
    opacity: .5
    flex-grow: 100%

  &__date
    margin-top: auto
</style>
