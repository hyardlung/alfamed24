<template>
  <main class="main">
    <section class="hero">
      <img src="@/assets/hero-ellipse.svg" alt="" class="hero__img" />
      <img
        src="@/assets/hero-ellipse_mobile.svg"
        alt=""
        class="hero__img_mobile"
      />
      <div class="container hero__content">
        <div class="hero__text-wrapper">
          <h1 class="title title_large hero__title">
            Мы работаем ради вашей улыбки
          </h1>
          <p class="hero__subtitle">Центр дентальной имплантации</p>
          <VButton :w="243" :h="69" class="hero__btn" />
        </div>
        <div class="hero__img-wrapper">
          <div class="">
            <img
              src="@/assets/persons/person-1.jpg"
              alt=""
              class="hero__person"
            />
          </div>
          <div class="">
            <img
              src="@/assets/persons/person-2.jpg"
              alt=""
              class="hero__person"
            />
          </div>
          <div class="">
            <img
              src="@/assets/persons/person-3.jpg"
              alt=""
              class="hero__person"
            />
          </div>
        </div>
      </div>
    </section>

    <section id="services" ref="services" class="services">
      <div class="container services__content">
        <h2 class="title title_small">Услуги</h2>
        <div class="services__cards">
          <v-card
            v-for="(card, idx) in servicesCards"
            :key="idx"
            isServiceCard
            :title="card.title"
            :text="card.text"
          ></v-card>
        </div>
      </div>
    </section>

    <section id="stocks" class="stocks">
      <div class="container stocks__container">
        <h2 class="title title_small">Акции и скидки</h2>
        <Carousel :settings="stocksSettings" :breakpoints="stocksBreakpoints">
          <Slide v-for="card in stocksCards" :key="card">
            <v-card
              isStockCard
              :imageUrl="card.img"
              :amount="card.price.amount"
              :description="card.price.descr"
              :title="card.title"
              :estimate="card.estimate"
            ></v-card>
          </Slide>
          <template #addons>
            <Navigation />
            <Pagination />
          </template>
        </Carousel>
      </div>
    </section>

    <section id="action" class="action">
      <div class="container action__container">
        <div class="action__content">
          <h2 class="title title_small action__title">
            Запись на консультацию
          </h2>
          <form action="" class="action__form">
            <fieldset class="action__fields">
              <v-text-input placeholder="Имя и фамилия" />
              <v-text-input placeholder="+7 (___)___-__-__" :w="200" />
            </fieldset>
            <VButton isInverted />
          </form>
          <p class="action__notice">
            Нажимая кнопку Записаться, вы даёте согласие на обработку
            персональных данных, соглашаясь с политикой конфиденциальности
          </p>
        </div>
      </div>
    </section>

    <section id="team" class="specialists">
      <div class="container specialists__container">
        <h2 class="title title_small">Ведущие специалисты клиники</h2>
        <div class="specialists__cards">
          <v-specialist-card
            v-for="(card, idx) in specialists"
            :key="idx"
            :photo="card.photo"
            :experience="card.experience"
            :fullname="card.fullname"
            :profession="card.profession"
          />
        </div>
      </div>
    </section>

    <section id="reviews" class="reviews">
      <div class="container reviews__container">
        <h2 class="title title_small">Отзывы</h2>
        <Carousel :itemsToShow="3" :wrapAround="true" :snapAlign="'start'">
          <Slide v-for="item in reviews" :key="item">
            <v-review
              :image="item.image"
              :fullname="item.fullname"
              :text="item.text"
              :date="item.date"
            ></v-review>
          </Slide>
          <template #addons>
            <Navigation />
            <!-- <Pagination /> -->
          </template>
        </Carousel>
      </div>
    </section>

    <section id="contacts" class="contacts">
      <div class="container contacts__container">
        <h2 class="title title_small">Контакты</h2>
        <div class="contacts__wrapper">
          <v-contact
            v-for="contact in contacts"
            :key="contact"
            :icon="contact.icon"
            :title="contact.title"
            :content="contact.content"
            :id="contact.id"
          />
        </div>
      </div>
    </section>

    <section id="map" class="map">
      <yandexMap
        :coordinates="coordinates"
        :detailed-controls="detailedControls"
        :controls="controls"
        map-type="hybrid"
      />
    </section>
  </main>
</template>

<script setup>
import { ref, onMounted } from "vue";
import "vue3-carousel/dist/carousel.css";
import { Carousel, Slide, Pagination, Navigation } from "vue3-carousel";

import VButton from "@/components/VButton.vue";
import VCard from "@/components/VCard.vue";
import VSpecialistCard from "@/components/VSpecialistCard.vue";
import VTextInput from "@/components/VTextInput.vue";
import VReview from "@/components/VReview.vue";
import VContact from "@/components/VContact.vue";

import { SERVICES_CARDS, STOCKS_CARDS } from "@/data/cards";
import { SPECIALISTS } from "@/data/specialists";
import { REVIEWS } from "@/data/reviews";
import { CONTACTS } from "@/data/contacts";
import arrow from "@/assets/Arrow_Circle_Right.svg";

import { yandexMap } from "vue-yandex-maps";
const coordinates = [55, 33];
const controls = ["fullscreenControl"];
const detailedControls = { zoomControl: { position: { right: 10, top: 50 } } };

const servicesCards = ref(SERVICES_CARDS);
const stocksCards = ref(STOCKS_CARDS);
const specialists = ref(SPECIALISTS);
const reviews = ref(REVIEWS);
const contacts = ref(CONTACTS);
// const arrow = ref(arrow);
const stocksSettings = ref({
  itemsToShow: 3,
  modelValue: 2,
  wrapAround: true,
});
const stocksBreakpoints = ref({
  888: {
    itemsToShow: 3,
    snapAlign: "start",
  },
  768: {
    itemsToShow: 2.3,
    snapAlign: "start",
  },
  640: {
    itemsToShow: 2.1,
    snapAlign: "start",
  },
  320: {
    itemsToShow: 2,
    snapAlign: "start",
  },
});

onMounted(() => {
  replaceCarouselIcons();
});

function replaceCarouselIcons() {
  const arrowNext = document.querySelectorAll(".carousel__next");
  const arrowPrev = document.querySelectorAll(".carousel__prev");
  arrowNext.forEach((item) => {
    item.innerHTML = `<img src="${arrow}" class="" />`;
  });
  arrowPrev.forEach((item) => {
    item.innerHTML = `<img src="${arrow}" style="transform: rotate(180deg);" />`;
  });
}

</script>

<style lang="sass" scoped>
.hero
  position: relative
  padding: 30px 0
  background-color: $gray
  overflow: hidden

  .container
    position: relative
    z-index: 1

  &__content
    display: flex
    padding: 156px 30px 102px
    gap: 30px
    @media screen and (max-width: 888px)
      flex-direction: column
      padding: 90px 30px 0

  &__text-wrapper
    max-width: 454px
    @media screen and (max-width: 1023px)
      max-width: 400px
      width: 100%

  &__img-wrapper
    display: flex
    gap: 20px
    margin-top: 25px
    height: min-content
    div
      max-width: 200px
      border-radius: 129px
      overflow: hidden
      img
        width: 100%
        height: 100%
        object-fit: cover

  &__title
    margin-bottom: 30px

  &__img
    width: 50vw
    position: absolute
    top: 0
    right: 0
    filter: drop-shadow(33px 92px 38px rgba(222, 62, 62, 0.57))
    &_mobile
      display: none
    @media screen and (max-width: 888px)
      display: none
      &_mobile
        position: absolute
        bottom: -116vw
        display: initial
        width: 100%

  &__subtitle
    max-width: 300px
    font-size: 26px
    line-height: 26px
    opacity: .7
    @media screen and (max-width: 767px)
      font-size: 24px
      line-height: 29px

  &__btn
    margin-top: 40px
    @media screen and (max-width: 767px)
      margin-top: 30px
      max-width: 320px
      width: 100% !important
      border-radius: 20px !important

.services
  padding: 60px 0
  @media screen and (max-width: 767px)
    padding: 30px 0

  &__cards
    margin-top: 60px
    display: grid
    grid-template: repeat(2, 1fr) / repeat(3, 1fr)
    gap: 30px
    @media screen and (max-width: 1023px)
      grid-template: repeat(3, 1fr) / repeat(2, 1fr)
    @media screen and (max-width: 888px)
      gap: 18px
    @media screen and (max-width: 767px)
      margin-top: 30px


.stocks
  padding: 60px 0
  &__container
    padding: 15px

  .title
    padding: 0 15px
    margin-bottom: 60px

.action
  padding: 60px 30px

  &__container
    max-width: 1120px
    padding: 60px 30px
    border-radius: 20px
    background: linear-gradient(3.33deg, #DE383D 2.15%, #DE6E3F 70.29%)

  &__content
    margin: 0 auto
    display: flex
    flex-direction: column
    align-items: center
    gap: 40px
    max-width: 837px
    color: $white

  &__form
    display: flex
    gap: 30px

  &__fields
    display: flex
    gap: 30px
    border: none

  &__notice
    max-width: 563px
    text-align: center
    font-family: 'Open Sans', sans-serif

.specialists
  padding: 64px 0 60px

  &__cards
    margin-top: 60px
    display: grid
    grid-template-columns: repeat(3, 1fr)
    gap: 30px

.reviews
  padding: 60px 0

  &__container
    padding: 15px

  .title
    margin-bottom: 60px
    padding: 0 15px

.contacts
  padding: 35px 0 60px

  &__wrapper
    margin-top: 60px
    display: grid
    grid-template-columns: repeat(3, 1fr)
    gap: 30px


.yandex-container
  height: 400px
</style>
