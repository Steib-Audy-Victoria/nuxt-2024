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
  position: fixed;
  padding: 20px;
  background-color: orange;
  top: 0;
  left: 0;
  right: 0;
  display: flex;
  flex-flow: row wrap;
  justify-content: space-between;
  font-size: 24px;
}
</style>
