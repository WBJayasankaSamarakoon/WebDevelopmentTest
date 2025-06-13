<template>
  <div class="hero">
    <div class="hero-background">
      <div class="slider">
        <img v-for="(image, index) in images" 
             :key="index" 
             :src="image.src" 
             :alt="image.alt"
             :class="{ active: currentIndex === index }">
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import '/src/styles/Hero.css'

const images = [
  { src: "/src/assets/Images/HeaderImage.jpg", alt: "Cinema Hero 1" },
  { src: "/src/assets/Images/HeaderImage2.jpg", alt: "Cinema Hero 2" },
  { src: "/src/assets/Images/HeaderImage3.jpg", alt: "Cinema Hero 3" }
];

const currentIndex = ref(0);

onMounted(() => {
  setInterval(() => {
    currentIndex.value = (currentIndex.value + 1) % images.length;
  }, 5000); 
});
</script>

<style scoped>

</style>