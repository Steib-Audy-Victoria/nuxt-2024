<script setup>
const props = defineProps({
  id: Number,
  title: String,
  description: String,
  image: String,
});

const store = useGlobalStore();

// Méthode 1
// const isAlreadyInCart = (id) => {
//   return store.cart.includes(id);
// };

// Méthode 2 (avec computed)
const buttonLabel = computed(() =>
  store.isInCart(props.id) ? "Remove from cart" : "Add to cart"
);
const onClick = () => {
  if (store.isInCart(props.id)) {
    store.removeFromCart(props.id);
  } else {
    store.addToCart(props.id);
  }
};
</script>

<template>
  <div class="c-recipe-card">
    <div class="c-recipe-card__image">
      <img src="" alt="" />
    </div>

    <div class="c-recipe-card__content">
      <p class="c-recipe-card__title">{{ title }}</p>
      <p class="c-recipe-card__description">{{ description }}</p>
      <RouterLink :to="`/recipes/${id}`">Plus d'infos</RouterLink>

      <!-- Méthode 1
        <div
        v-if="!isAlreadyInCart(id)"
        class="c-recipe-card__button"
        @click="store.addToCart(id)"
      >
        Add to cart
      </div>
      <div
        v-else
        class="c-recipe-card__button"
        @click="store.removeFromCart(id)"
      >
        Remove from cart
      </div> -->

      <!-- Méthode 2 -->
      <div class="c-recipe-card__button" @click="onClick(id)">
        {{ buttonLabel }}
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.c-recipe-card {
  background-color: white;
  box-shadow: 0 0 31px 0 rgba(0, 0, 0, 0.05);
  border-radius: 10px;

  &__content {
    display: flex;
    flex-flow: column wrap;
    align-items: flex-start;
    padding: 20px;
  }

  &__image {
    width: 100%;
    height: 100px;
    background-color: lightgrey;
  }

  &__title {
    font-size: 22px;
    line-height: 1.2;
    color: black;
    &:not(:first-child) {
      margin-top: 10px;
    }
  }

  &__description {
    font-size: 16px;
    color: black;
    line-height: 1.2;
    &:not(:first-child) {
      margin-top: 10px;
    }
  }

  &__button {
    display: inline-block;
    background-color: orange;
    color: white;
    padding: 10px 20px;
    border-radius: 10px;
    cursor: pointer;
    &:not(:first-child) {
      margin-top: 30px;
    }
  }
}
</style>
