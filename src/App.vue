<script setup lang="ts">
import SampleApp from "./components/SampleApp.vue";
</script>

<template>
  <header>
    <div class="wrapper">
      <SampleApp msg="Mind Lens Vue Coding Assignment" />
    </div>
  </header>
</template>

<style scoped>
header {
  line-height: 1.5;
  margin-top: 1rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
