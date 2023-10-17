<script setup>
const props = defineProps({
  error: Object,
});
</script>

<template>
  <div class="p-error">
    <p>Erreur : Page introuvable</p>
    {{ error }}
  </div>
</template>

<style lang="scss"></style>
