<template>
  <button
    :class="['button', isInverted ? 'button_color_white' : 'button_color_red']"
    :style="[{ width: w + 'px' }, { height: h + 'px' }]"
  >
    {{ title }}
  </button>
</template>
<script setup>
defineProps({
  isInverted: {
    type: Boolean,
    default: false,
  },
  title: {
    type: String,
    default: "Записаться",
  },
  w: {
    type: Number,
    default: 213,
  },
  h: {
    type: Number,
    default: 59,
  },
});
// export default {
//   props: {
//     isInverted: {
//       type: Boolean,
//       default: false,
//     },
//     title: {
//       type: String,
//       default: "Записаться",
//     },
//     w: {
//       type: Number,
//       default: 213,
//     },
//     h: {
//       type: Number,
//       default: 59,
//     },
//   },
//   data() {
//     return {};
//   },
// };
</script>
<style lang="sass" scoped>
.button
  display: flex
  align-items: center
  justify-content: center
  font-size: 24px
  line-height: 29px
  font-weight: 400
  font-family: 'Open Sans', sans-serif
  cursor: pointer
  border-radius: 10px
  border: none
  overflow: hidden
  transition: all .3s ease-in-out

  &_color
    &_red
      color: $white
      background: $red
      &:hover
        background: #C8171D
    &_white
      color: $red
      background-color: $white

  &-inverted
    background: green

@media screen and (max-width: 1023px)
  .button
    font-size: 20px
</style>
