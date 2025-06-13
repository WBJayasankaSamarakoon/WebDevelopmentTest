<template>
  <div class="hamburger-menu">
    <button @click="toggleMenu" class="hamburger-button">
      <img v-if="!isOpen" src="/src/assets/Icons/MenuWhite.svg" alt="Menu" class="menu-icon">
      <span v-else class="close-icon">×</span>
    </button>
    
    <div v-if="isOpen" class="mobile-nav-links">
      <ul>
        <li><a href="#" @click="toggleMenu">LOCATION & CONTACT</a></li>
        <li><a href="#" @click="toggleMenu">GALLERY</a></li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import '/src/styles/HamburgerMenu.css'

const isOpen = ref(false);

function toggleMenu() {
  isOpen.value = !isOpen.value;
}
</script>
