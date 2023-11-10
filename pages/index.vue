<script setup>
const env = useRuntimeConfig();

const { client } = usePrismic();

const { data: home, error } = await useAsyncData("home", () =>
  client.getSingle("homepage")
);

const { data: recipes } = await useAsyncData("recipes", () => {
  return $fetch(env.public.apiUrl + "/recipes");
});

// Handle case when request fails
if (!home.value || error.value) {
  throw createError({
    statusCode: 404,
    statusMessage: "La page d'accueil est introuvable",
  });
}
</script>

<template>
  <!--Section Hero-->
  <Hero
    :title="home.data.hero_title"
    :text="home.data.hero_text"
    :buttons="home.data.hero_buttons"
  />

  <!--Section Information-->
  <section class="Information">
    <Information :information="home.data.information" />
  </section>

  <!--Section Recipes-->
  <section class="product">
    <myTitle
      :title="home.data.product_title"
      :sub_title="home.data.product_sub_title"
    />
    <div class="product__recipes">
      <div class="product__recipe" v-for="recipe in recipes">
        <MyBigCardMenu
          v-bind="{
            id: recipe.recipe_id,
            title: recipe.recipe_name,
            imageSrc: recipe.image_url,
            imageAlt: recipe.image_alt,
            price: recipe.price,
            note: recipe.note,
          }"
        />
      </div>
    </div>
  </section>

  <!-- Section Recipes
    <section class="product">
      <myTitle
        :title="home.data.product_title"
        :sub_title="home.data.product_sub_title"
      />
      <div class="product__recipes">
        <div class="product__recipe" v-for="recipe in recipes">
          <RecipeCard
            v-bind="{
              id: recipe.recipe_id,
              title: recipe.recipe_name,
              description: recipe.recipe_description,
            }"
          />
        </div>
      </div>
    </section> -->

  <section class="services">
    <myTitle
      :title="home.data.services_title"
      :sub_title="home.data.services_sub_title"
    />
    <!-- <Services :services="home.data.services" /> -->
  </section>

  <section class="work">
    <myTitle
      :title="home.data.how_to_work_title"
      :sub_title="home.data.how_to_work_sub_title"
    />

    <Work :infos="home.data.how_to_work" />
  </section>

  <section class="testimonials">
    <myTitle
      :sub_title="home.data.testimonials_sub_title"
      :title="home.data.testimonials_title"
    />
    <Avis />
  </section>

  <section class="Contact">
    <MyNewsletter />
  </section>
</template>

<style lang="scss">
.Information {
  display: flex;
  justify-content: center;
  align-items: center;
  padding-top: rem(30);
}

.product {
  padding-top: rem(50);
  &__recipes {
    display: grid;
    place-items: center;
    grid-template-columns: repeat(3, 1fr);
    gap: 30px;
    margin-top: 50px;
  }
}

.services {
  padding-top: rem(50);
}

.work {
  padding-top: rem(50);
}

.testimonials {
  padding-top: rem(50);
}

.Contact {
  display: flex;
  justify-content: center;
  align-items: center;
  padding-top: rem(50);
  padding-bottom: rem(50);
}
</style>
