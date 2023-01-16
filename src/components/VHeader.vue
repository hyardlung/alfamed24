<template>
  <header class="header">
    <div class="header__inner">
      <router-link to="/" class="header__logo">
        <img src="../assets/logo.svg" alt="" class="header__img" />
      </router-link>
      <nav class="header__nav is-desktop">
        <a href="#" v-scroll-to="'#services'" class="header__link">Услуги</a>
        <a href="#" v-scroll-to="'#stocks'" class="header__link">Акции</a>
        <a href="#" v-scroll-to="'#team'" class="header__link">Команда</a>
        <a href="#" v-scroll-to="'#reviews'" class="header__link">Отзывы</a>
        <a href="#" v-scroll-to="'#contacts'" class="header__link">Контакты</a>
      </nav>
      <v-button class="is-desktop" />
      <button
        :class="['burger', 'is-mobile', { 'is-open': isOpen }]"
        @click="handleBurger"
      >
        <div class="burger__wrap">
          <span class="burger__line burger__line_first"></span>
          <span class="burger__line burger__line_second"></span>
          <span class="burger__line burger__line_third"></span>
          <span class="burger__line burger__line_fourth"></span>
        </div>
      </button>
    </div>
  </header>

  <div
    :class="['overlay', { active: isOpen }]"
    @wheel.prevent
    @touchmove.prevent
    @scroll.prevent
  >
    <nav class="header__nav is-mobile">
      <a
        href="#"
        v-scroll-to="'#services'"
        @click="handleBurger"
        class="header__link"
        >Услуги</a
      >
      <a
        href="#"
        v-scroll-to="'#stocks'"
        @click="handleBurger"
        class="header__link"
        >Акции</a
      >
      <a
        href="#"
        v-scroll-to="'#team'"
        @click="handleBurger"
        class="header__link"
        >Команда</a
      >
      <a
        href="#"
        v-scroll-to="'#feedback'"
        @click="handleBurger"
        class="header__link"
        >Отзывы</a
      >
      <a
        href="#"
        v-scroll-to="'#contacts'"
        @click="handleBurger"
        class="header__link"
        >Контакты</a
      >
      <v-button :w="320" :h="64" class="burger-button" />
    </nav>
  </div>
</template>

<script setup>
import { ref } from "vue";
import VButton from "./VButton.vue";

const isOpen = ref(false);

function handleBurger() {
  isOpen.value = !isOpen.value;
}
</script>

<style lang="sass" scoped>
.overlay
  position: absolute
  top: 0
  right: 0
  bottom: 0
  left: 0
  z-index: 90
  visibility: hidden
  opacity: 0
  transition: all .3s ease-in-out
  background: rgba(226, 183, 183, 0.5)
  box-shadow: 0 8px 32px 0 rgba(226, 183, 183, 0.5)
  backdrop-filter: blur(10px)
  -webkit-backdrop-filter: blur(10px)
  &:after
    content: ''
    top: 0
    right: 0
    bottom: 0
    left: 0
  &.active
    visibility: visible
    opacity: 1

.header
  position: absolute
  top: 30px
  right: 30px
  left: 30px
  margin: 0 auto
  max-width: 1100px
  z-index: 100

  &__inner
    padding: 10px
    display: flex
    align-items: center
    justify-content: space-between
    gap: 20px
    background: $white
    border-radius: 20px

  &__logo
    display: block
    height: 36px
    max-width: 224px
    min-width: 200px
    img
      width: 100%

  &__nav
    display: flex
    column-gap: 30px
    &.is-mobile
      display: flex
      flex-direction: column
      margin-top: 110px
      padding: 0 30px
      .header__link
        background-color: $white

  &__link
    position: relative
    font-family: 'Open Sans'
    font-size: 20px
    line-height: 24px
    color: $black
    opacity: .7
    text-decoration: none
    transition: all .2s ease-in-out
    &:hover
      color: $red

.burger
  position: relative
  display: flex
  align-items: center
  justify-content: center
  width: 40px
  height: 40px
  padding: 12px
  border: none
  border-radius: 50%
  background-color: $red
  cursor: pointer

  &__wrap
    position: relative
    width: 100%
    height: 12px

  &__line
    position: absolute
    left: 0
    width: 16px
    height: 2px
    border-radius: 2px
    background-color: $white
    transition: all .3s ease-in-out
    &_first
      top: 0
    &_second, &_third
      top: 50%
      transform: translateY(-50%)
    &_fourth
      bottom: 0

.is-open .burger__line_first, .is-open .burger__line_fourth
  opacity: 0
.is-open .burger__line_second
  transform: translateY(-50%) rotate(45deg)
.is-open .burger__line_third
  transform: translateY(-50%) rotate(-45deg)

.is-desktop
  display: flex
.is-mobile
  display: none

@media screen and (max-width: 1023px)
  .header
    &__link
      font-size: 16px

@media screen and (max-width: 888px)
  .header
    &__nav
      flex-wrap: wrap

@media screen and (max-width: 767px)
  .header
    &__nav
      row-gap: 15px
    &__link
      padding: 20px 15px
      border-radius: 20px
      opacity: 1

  .burger-button
    margin: 5px auto 0
    border-radius: 20px

  .is-desktop
    display: none
  .is-mobile
    display: flex
</style>
