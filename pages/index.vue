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
  <div class="p-index">
    <p>Page d'accueil</p>
    <!-- <RecipeCard
      v-bind="{ title: 'Titre de la recette', description: 'une description' }"
    /> -->
    <!-- <prismic-rich-text class="p-index__content" :field="home.data.hero_title" /> -->
    <Hero
      :title="home.data.hero_title"
      :text="home.data.hero_text"
      :buttons="home.data.hero_buttons"
    />
    <Information :information="home.data.information" />

    <div class="p-index__recipes">
      <div class="p-index__recipe" v-for="recipe in recipes">
        <RecipeCard
          v-bind="{
            id: recipe.recipe_id,
            title: recipe.recipe_name,
            description: recipe.recipe_description,
          }"
        />
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.p-index {
  &__recipes {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 30px;
    margin-top: 50px;
  }
}
</style>
