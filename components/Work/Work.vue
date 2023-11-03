<script setup>
const props = defineProps({
  infos: Array,
});
</script>

<template>
  <section class="sectionWork">
    <div class="workLine workLine-1">
      <WorkLine num="1" />
    </div>
    <div class="workLine workLine-2">
      <WorkLine num="2" />
    </div>

    <div class="workEtap" v-for="i in infos">
      <div class="workEtap__img">
        <PrismicImage class="img" :field="i.how_to_work_image" />
      </div>

      <div>
        <PrismicText
          class="workEtap__title"
          :field="i.how_to_work_title_field"
        />
        <PrismicRichText class="workEtap__text" :field="i.how_to_work_text" />
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.sectionWork {
  position: relative;
  display: flex;
  gap: 0 8%;

  .workEtap {
    z-index: 1;
    display: flex;
    gap: 25px;
    flex-direction: column;
    min-width: min-content;
    width: fit-content;
    max-width: 400px;

    &__img {
      width: 100%;
      text-align: center;

      .img {
        width: 85%;
      }
    }

    &__title {
      text-transform: uppercase;
      margin-bottom: 25px;
    }
  }

  > :nth-child(2n) {
    flex-direction: column-reverse;

    .workEtap__title {
      text-align: center;
    }
  }

  > :last-child {
    text-align: right;
  }

  .workLine {
    position: absolute;
    z-index: 0;
    width: 400px;

    &-1 {
      top: 10%;
      left: 10%;
    }

    &-2 {
      top: 10%;
      right: 10%;
    }
  }
}
</style>
