<template>
  <div class="specialist">
    <img :src="getPhoto(photo)" :alt="fullname" class="specialist__photo" />
    <div class="specialist__info">
      <p class="specialist__experience">Стаж {{ experience }} {{ ending }}</p>
      <h3 class="specialist__fullname">{{ fullname }}</h3>
      <p class="specialist__profession">{{ profession }}</p>
    </div>
  </div>
</template>
<script setup>
import { ref, onMounted } from "vue";
const props = defineProps({
  photo: {
    type: String,
    required: true,
  },
  experience: {
    type: Number,
    required: true,
  },
  fullname: {
    type: String,
    required: true,
  },
  profession: {
    type: String,
    required: true,
  },
});

const ending = ref("");

onMounted(() => {
  makeEnding(props.experience);
});

function makeEnding(exp) {
  let last = Number(exp.toString().slice(-1));
  if (last === 1 && exp !== 11) return (ending.value = "год");
  if (last >= 2 && last < 5 && exp !== 12 && exp !== 13)
    return (ending.value = "года");
  else return (ending.value = "лет");
}

function getPhoto(photo) {
  return "src/assets/specialists/" + photo;
}
</script>

<style lang="sass" scoped>
.specialist
  max-width: 353px
  display: flex
  flex-direction: column
  gap: 20px
  font-family: 'Open Sans', serif
  font-size: 20px
  line-height: 24px
  @media screen and (max-height: 767px)
    align-items: center

  &__photo
    width: 100%
    border-radius: 20px
    object-fit: cover
    @media screen and (max-height: 767px)

  &__info
    display: flex
    flex-direction: column
    gap: 10px

  &__experience
    color: $red

  &__fullname
    font-family: 'Lora', serif
    font-size: 26px
    line-height: 26px
</style>
