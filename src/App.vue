<template>
  <header>
    <NavBarComp />
  </header>
  <main class="container">
    <Section1Comp />
  </main>
  <FooterComp />
</template>
<script setup>
import NavBarComp from "./components/NavBarComp.vue";
import FooterComp from "./components/FooterComp.vue";
import Section1Comp from "./components/Section1Comp.vue";
</script>
<style scoped>
main {
  min-height: 100vh;
}
</style>
