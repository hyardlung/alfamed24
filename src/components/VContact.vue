<template>
  <div class="contact">
    <img :src="getIcons(icon)" :alt="title" class="contact__icon" />
    <span class="contact__title">{{ title }}</span>
    <p class="contact__content">{{ content }}</p>
  </div>
</template>
<script setup>
defineProps(["icon", "title", "content", "hours"]);

function getIcons(icon) {
  return "src/assets/icons/" + icon;
}
</script>
<style lang="sass" scoped>
.contact
  padding: 20px
  display: flex
  flex-direction: column
  gap: 15px
  // height: 243px
  font-family: 'Open Sans', sans-serif
  background-color: $gray
  border-radius: 20px

  &__icon
    width: 75px

  &__title
    font-family: 'Lora', serif
    font-size: 32px
    line-height: 32px

  &__content
    margin-top: auto
    font-size: 20px
    line-height: 24px

#tel
  background: none
  outline: 4px solid $red

  .contact__content
    max-width: 180px

#address
  .contact__content
      max-width: 280px

#hours
  .contact__content
      max-width: 170px
</style>
