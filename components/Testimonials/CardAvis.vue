<script setup>
const props = defineProps({
  donnees: Array,
});
</script>

<template>
  <div class="cardAvis">
    <div class="cardAvis__personne">
      <PrismicImage class="cardAvis__pp" :field="donnees.photo" />
      <div class="cardAvis__desc">
        <PrismicText class="h5" :field="donnees.prenom" />
        <PrismicRichText class="p2" :field="donnees.job" />
      </div>
    </div>

    <PrismicRichText class="cardAvis__avis" :field="donnees.commentaire" />
  </div>
</template>

<style lang="scss" scoped>
.cardAvis {
  flex: none;
  display: grid;
  place-items: center;
  gap: 5px;
  width: 100%;
  padding: 60px 20px;
  aspect-ratio: 2/1;

  &__personne {
    display: flex;
    align-items: center;
    gap: 10px;
    margin: auto;
    width: fit-content;

    .cardAvis__pp {
      width: 76px;
      aspect-ratio: 1/1;
      object-fit: cover;
      border-radius: 100%;
    }

    .cardAvis__desc {
      > * {
        margin: 5px 0;
      }
    }
  }

  &__avis {
    width: 85%;
    margin: auto;
    text-align: center;

    ::before,
    ::after {
      content: '"';
      display: inline;
    }
  }
}
</style>
