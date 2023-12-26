<template>
  <footer class="footer">
    <div class="footer__container">
      <a href="/">
        <img src="../assets/logo-white.svg" alt="footer logo" />
      </a>
      <div class="footer__content">
        <a href="" class="footer__link">Политика конфиденциальности</a>
        <a href="" class="footer__link">Условия использования</a>
        <p class="footer__copyright">
          2019 © «Альфамед» - клиника современных технологий Общество
          с ограниченной ответственностью «Медтех»
        </p>
      </div>
    </div>
  </footer>
</template>

<script setup></script>

<style lang="sass" scoped>
.footer
  margin: 60px auto 30px
  padding: 30px
  max-width: 1160px
  font-family: 'Open Sans', sans-serif
  font-size: 16px
  line-height: 120%
  color: rgba(255, 255, 255, .7)

  &__container
    padding: 30px
    display: flex
    justify-content: space-between
    gap: 30px
    background: $red
    border-radius: 20px

    a
      width: max-content

    @media screen and (max-width: 767px)
      padding: 20px
      flex-direction: column


  &__content
    max-width: 528px
    display: flex
    flex-direction: column
    gap: 10px
    @media screen and (max-width: 767px)
      font-size: 12px

  &__link
    font-size: 20px
    line-height: 120%
    color: $white
    text-decoration: underline

    @media screen and (max-width: 767px)
      font-size: 12px
</style>
