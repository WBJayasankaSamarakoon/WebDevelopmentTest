<template>
  <header class="header">
    <!-- Navigation -->
    <div class="nav-container">
      <img src="/src/assets/Logos/LogoWhite.svg" alt="Logo" class="logo" />
      
      <!-- Desktop Navigation -->
      <nav class="nav-links desktop-nav">
        <ul>
          <li><a href="#">HOME</a></li>
          <li><a href="#">OUR SCREENS</a></li>
          <li><a href="#">SCHEDULE</a></li>
          <li><a href="#" class="active">MOVIE LIBRARY</a></li>
          <li><a href="#">LOCATION & CONTACT</a></li>
           <li class="menu-icon-desktop" @click="toggleDesktopMenu">
            <img src="/src/assets/Icons/MenuWhite.svg" alt="Menu Icon" />
          </li>
        </ul>
      </nav>
      
      <!-- Mobile Hamburger Menu -->
      <HamburgerMenu class="mobile-menu" />
    </div>

    <!-- Hero Section -->
    <Hero />
  </header>
</template>

<script setup>
import HamburgerMenu from './HamburgerMenu.vue';
import Hero from './Hero.vue';
import '/src/styles/Header.css';

</script>

<style scoped>
</style>