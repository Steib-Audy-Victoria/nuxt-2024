<template>
  <div class="title">
    <PrismicText class="h3" :field="sub_title" />
    <PrismicText class="h2" :field="title" />
  </div>
</template>

<style lang="scss" scoped>
.title {
  text-align: center;
  line-height: 1.5;
  margin-bottom: 57px;

  .h2 {
    font-size: rem(30);
    font-weight: 700;
    font-family: $primary-font-family;
  }

  .h3 {
    font-size: rem(15);
    font-family: $primary-font-family;
    color: $primary-color;
  }
}
</style>

<script setup>
defineProps({
  title: String,
  sub_title: String,
});
</script>
