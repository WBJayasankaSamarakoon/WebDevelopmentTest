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
</script>

<style scoped>
.header {
  position: relative;
  width: 100%;
  font-family: sans-serif;
  color: white;
}

/* Navigation */
.nav-container {
  position: absolute;
  top: 0;
  width: 95%;
  z-index: 10;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.2rem 2rem;
}

.logo {
  width: 180px;
}

.nav-links ul {
  list-style: none;
  display: flex;
  gap: 1.8rem;
  margin: 0;
  padding: 0;
}

.nav-links ul li a {
  color: white;
  text-decoration: none;
  font-weight: 500;
  letter-spacing: 0.05em;
  transition: color 0.3s ease;
  position: relative;
}

.nav-links ul li a:hover,
.nav-links ul li a.active {
  color: #fdd835;
}

/* Hover effect - underline animation */
.nav-links ul li a::after {
  content: '';
  position: absolute;
  width: 0;
  height: 2px;
  bottom: -4px;
  left: 0;
  background-color: #fdd835;
  transition: width 0.3s ease;
}

.nav-links ul li a:hover::after,
.nav-links ul li a.active::after {
  width: 100%;
}

/* Mobile menu - hidden by default */
.mobile-menu {
  display: none;
}

/* Responsive */
@media (max-width: 768px) {
  .desktop-nav {
    display: none;
  }
  
  .mobile-menu {
    display: block;
  }
  
  .logo {
    width: 120px;
  }
}
</style>