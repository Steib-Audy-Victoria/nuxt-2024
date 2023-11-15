<script setup>
const props = defineProps({
  services: Array,
});
</script>

<template>
  <section class="services">
    <div v-for="item in services" class="services__item">
      <div class="services__icon">
        <MyIconGlobale
          v-if="item.services_icon === 'Livraison'"
          name="Livraison"
          background="secondary"
          color="primary"
          size="big"
        />
        <MyIconGlobale
          v-else-if="item.services_icon === 'Repas'"
          name="Repas"
          background="secondary"
          color="primary"
          size="big"
        />
        <MyIconGlobale
          v-else
          name="Fourchette"
          background="secondary"
          color="primary"
          size="big"
        />
      </div>
      <div class="services__content">
        <div class="services__content-title">
          <PrismicRichText :field="item.services_title" />
        </div>
        <div class="services__content-text">
          <PrismicRichText :field="item.services_text" />
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss">
.services {
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: rem(50);

  &___content {
    &-title {
      text-align: center;
    }
  }

  &__item {
    max-width: rem(320);
    min-width: rem(300);
    max-height: rem(320);
    min-height: rem(300);
    border-radius: rem(20);
    border: rem(1) solid $gray;
    overflow: hidden;
    padding: rem(20);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  &__icon {
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
</style>
