<script setup>
import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import Introduction from './components/Introduction.vue'
import MovieGrid from './components/MovieGrid.vue'
import ContactMap from './components/ContactMap.vue'
import Footer from './components/Footer.vue'
import HamburgerMenu from './components/HamburgerMenu.vue'
</script>

<template>
  <div class="app-wrapper">
    <Header />
    <main>
      <Introduction />
      <MovieGrid />
      <ContactMap />
    </main>
    <Footer />
  </div>
</template>

<style scoped>
</style>