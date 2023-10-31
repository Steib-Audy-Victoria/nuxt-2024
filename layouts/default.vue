<template>
  <main class="layout">
    <div class="layout__header">
      <MyHeader />
    </div>
    <aside class="layout__aside">
      <slot name="aside"></slot>
    </aside>
    <article class="layout__article">
      <NuxtPage />
    </article>

    <div class="layout__footer">
      <MyFooter />
    </div>
  </main>
</template>
<style lang="scss" scoped>
.layout {
  display: grid;
  grid-template:
    "header"
    "article"
    "aside"
    "footer";
  padding-top: 80px;

  @include medium-up {
    grid-template:
      "header header header"
      "article article aside"
      "footer footer footer";
  }

  > * {
    padding: rem(16);
  }
  &__article {
    grid-area: article;
  }
  &__aside {
    grid-area: aside;
  }
  &__footer {
    grid-area: footer;
  }
  &__header {
    grid-area: header;
  }
}
</style>
