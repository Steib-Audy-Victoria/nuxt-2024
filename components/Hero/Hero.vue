<script setup="">
const env = useRuntimeConfig();
const props = defineProps({
  title: Array,
  text: Array,
  buttons: Array,
});

const { data: recipes } = await useAsyncData("recipes", async () => {
  return $fetch(env.public.apiUrl + "/recipes");
});

// onMounted(async () => {
//   await getRecipes()
// })
</script>

<template>
  <section class="hero">
    <div class="hero__left">
      <div class="hero__left-delivery">
        <p>Bike Delivery</p>
        <img
          src="../../public/BikeDelivery.jpg"
          alt="illustration de livraison"
        />
      </div>
      <div class="hero__title">
        <!-- Convert prismic rich text field to full html text -->
        <PrismicRichText :field="title" />
      </div>
      <div class="hero__text">
        <!-- Convert prismic rich text field to full html text -->
        <PrismicRichText :field="text" />
      </div>
      <div class="hero__buttons">
        <div v-for="button in buttons">
          <!-- v-if within the loop -->
          <!--        <button v-if="button.button_type === 'default'" class="hero__button -default">-->
          <!--          <a :href="button.button_link.url">{{ button.button_label }}</a>-->
          <!--        </button>-->
          <!--        <button v-else class="hero__button -video">-->
          <!--          <a :href="button.button_link.url">{{ button.button_label }}</a>-->
          <!--        </button>-->
          <!-- Or variant props inside <Button /> component to handle all possible cases-->
          <MyButton
            :href="button.button_link.url"
            :variant="button.button_type"
            >{{ button.button_label }}</MyButton
          >
        </div>
      </div>
    </div>

    <div class="hero__right">
      <MyCardMenu
        title="Burger"
        description="Mushroom Sauce"
        price="5.15"
        imageSrc="burger.png"
        imageAlt="Burger"
      />
      <MyCardMenu
        title="Food Combo"
        description="Mushroom Sauce"
        price="9.15"
        imageSrc="FoodCombo.png"
        imageAlt="Foode combo"
      />
      <MyCardMenu
        title="Pizza"
        description="Mushroom Sauce"
        price="6.15"
        imageSrc="pizza.png"
        imageAlt="Pizza"
      />
      <MyCardMenu
        title="Cake"
        description="Mushroom Sauce"
        price="5.15"
        imageSrc="cake.png"
        imageAlt="Cake"
      />
    </div>
  </section>
</template>

<style lang="scss">
.hero {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  max-width: 100vw;
  padding: rem(50) rem(30);

  &__left {
    display: flex;
    flex-direction: column;
    gap: rem(20);
    max-width: rem(700);

    &-delivery {
      width: 270px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 5px;
      padding: 5px;
      border-radius: 30px;
      background: $secondary-color;

      img {
        width: 54px;
        aspect-ratio: 1/1;
        object-fit: cover;
        border-radius: 100%;
      }

      p {
        color: $primary-color;
        margin-left: 25px;
      }
    }
  }

  &__title {
    font-size: 40px;
    font-weight: 700;
    line-height: 1.2;
    color: black;

    strong {
      color: orange;
    }
  }

  &__text {
    font-size: 18px;
    line-height: 1.1;
    color: black;
    &:not(:first-child) {
      margin-top: 1rem;
    }
  }

  &__buttons {
    display: flex;
    flex-flow: row wrap;
    align-items: center;
    gap: 5rem;
    &:not(:first-child) {
      margin-top: 2rem;
    }
  }

  &__button {
    &.-default {
      background-color: orange;
    }
  }

  &__right {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: rem(40);
  }
}
</style>
