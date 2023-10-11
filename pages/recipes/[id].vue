<script setup>
const route = useRoute();
</script>

<template>
  <div class="p-recipes-id">recette avec l'id : {{ route.params.id }}</div>
</template>

<style lang="scss"></style>
