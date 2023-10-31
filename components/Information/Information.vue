<script setup>
const props = defineProps({
  information: Array,
});
</script>

<template>
  <section class="information">
    <div v-for="item in information" class="information__item">
      <div class="information__icon">
        <img :src="`/icons/${item.information_icon}.svg`" alt="" />
      </div>
      <div class="information__title">
        <PrismicRichText :field="item.information_title" />
      </div>
      <div class="information__text">
        <PrismicRichText :field="item.information_text" />
      </div>
    </div>
  </section>
</template>

<style lang="scss">
.information {
  display: flex;
  flex-flow: row wrap;
  width: 100%;

  &__item {
    flex: 1;
    display: flex;
    flex-flow: column wrap;
    justify-content: center;
    align-items: center;
  }

  &__icon {
    display: inline-flex;
    width: 30px;
    height: 30px;
    padding: 10px;
    align-items: center;
    justify-content: center;
    background-color: orange;
    border-radius: 50%;
  }

  &__title {
    font-weight: 700;
    &:not(:first-child) {
      margin-top: 10px;
    }
  }

  &__text {
    &:not(:first-child) {
      margin-top: 10px;
    }
  }
}
</style>
