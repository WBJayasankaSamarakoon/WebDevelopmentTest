<template>
  <div class="hamburger-menu">
    <button @click="toggleMenu" class="hamburger-button">
      <img v-if="!isOpen" src="/src/assets/Icons/MenuWhite.svg" alt="Menu" class="menu-icon">
      <span v-else class="close-icon">×</span>
    </button>
    
    <div v-if="isOpen" class="mobile-nav-links">
      <ul>
        <li><a href="#" @click="toggleMenu">HOME</a></li>
        <li><a href="#" @click="toggleMenu">OUR SCREENS</a></li>
        <li><a href="#" @click="toggleMenu">SCHEDULE</a></li>
        <li><a href="#" @click="toggleMenu" class="active">MOVIE LIBRARY</a></li>
        <li><a href="#" @click="toggleMenu">LOCATION & CONTACT</a></li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const isOpen = ref(false);

function toggleMenu() {
  isOpen.value = !isOpen.value;
}
</script>

<style scoped>
.hamburger-menu {
  position: relative;
}

.hamburger-button {
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
}

.menu-icon {
  width: 24px;
  height: 24px;
}

.close-icon {
  font-size: 28px;
  color: white;
  display: block;
  line-height: 1;
}

.mobile-nav-links {
  position: fixed;
  top: 0;
  right: 0;
  width: 70%;
  height: 100vh;
  background: rgba(0, 0, 0, 0.9);
  z-index: 100;
  padding: 2rem;
  box-sizing: border-box;
  animation: slideIn 0.3s ease-out;
}

.mobile-nav-links ul {
  list-style: none;
  padding: 0;
  margin-top: 3rem;
}

.mobile-nav-links ul li {
  margin-bottom: 1.5rem;
}

.mobile-nav-links ul li a {
  color: white;
  text-decoration: none;
  font-size: 1.2rem;
  transition: color 0.3s ease;
}

.mobile-nav-links ul li a:hover,
.mobile-nav-links ul li a.active {
  color: #fdd835;
}

@keyframes slideIn {
  from {
    transform: translateX(100%);
  }
  to {
    transform: translateX(0);
  }
}
</style>