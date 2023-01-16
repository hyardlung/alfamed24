<template>
  <input
    type="text"
    class="input"
    :placeholder="placeholder"
    :style="`max-width: ${w ? w : 364}px`"
  />
</template>
<script>
export default {
  props: {
    placeholder: {
      type: String,
    },
    getMask: {
      type: String,
    },
    w: {
      type: Number,
    },
  },
  data() {
    return {
      name: "VTextInput",
    };
  },
};
</script>
<style lang="sass" scoped>
.input
  padding: 20px
  width: 100%
  height: 64px
  border: none
  border-radius: 10px
  font-family: 'Open Sans', sans-serif
  font-size: 20px
  line-height: 24px
  color: $white
  background-color: #E16E51
  transition: all .3s ease-in-out
  &::placeholder
    color: rgba(255, 255, 255, .8)
  &:is(:hover, :focus)
    background-color: #AC2C30
</style>
