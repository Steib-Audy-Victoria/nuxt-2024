<script setup>
import { useGlobalStore } from "@/stores/global.js";

const store = useGlobalStore();
</script>

<template>
  <header class="c-header">Le header</header>
  <div class="c-header__count" @click="store.increment()">
    {{ store.cart }}
  </div>
</template>

<style lang="scss">
.c-header {
  display: flex;
  flex-flow: row wrap;
  justify-content: space-between;
  font-size: 24px;
}
</style>
