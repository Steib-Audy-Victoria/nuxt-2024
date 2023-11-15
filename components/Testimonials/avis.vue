<script setup>
// import de Prismic
const { client } = usePrismic();
const { data: home, error } = await useAsyncData("home", () =>
  client.getSingle("homepage")
);

if (!home.value || error.value) {
  throw createError({
    statusCode: 404,
    statusMessage: "La page d'accueil est introuvable",
  });
}
</script>

<template>
  <section class="sectionAvis">
    <div class="sectionAvis__content">
      <CarrouselCardsAvis :donnees="home.data.card_avis" />
      <PrismicImage class="cardAvis__pp" :field="home.data.avis_img" />
    </div>
  </section>
</template>

<style lang="scss" scoped>
.sectionAvis {
  margin: rem(20);
  &__content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 45px;

    .cardAvis__pp {
      width: 50%;
    }
  }
}
</style>
