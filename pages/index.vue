<script setup></script>

<template>
  <div class="p-index">
    <p>Page d'accueil</p>
    <RecipeCard
      v-bind="{ title: 'Titre de la recette', description: 'une description' }"
    />
  </div>
</template>

<style lang="scss"></style>
