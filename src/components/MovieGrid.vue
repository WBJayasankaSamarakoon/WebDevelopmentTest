<template>
  <div class="movie-grid">
    <div class="header-container">
      <h2>Collect your favourites</h2>
      <div class="search-bar">
        <div class="search-wrapper">
          <button @click="searchMovies" class="search-icon-button">
            <img src="/src/assets/Icons/SearchWhite.svg" alt="Search" class="search-icon" />
          </button>
          <input
            type="text"
            v-model="searchQuery"
            @keyup.enter="searchMovies"
            placeholder="Search title and add to grid"
          />
        </div>
      </div>
    </div>

    <hr />

    <div class="movies-wrapper">
      <div class="movies">
        <div
          v-for="(movie, index) in movies"
          :key="movie.id || index"
          class="movie-card"
        >
          <img :src="movie.image" :alt="movie.title" />
          <button class="close-btn" @click="removeMovie(index)">✕</button>
          <div class="movie-info">
            <h3>{{ movie.title }}</h3>
            <p>{{ movie.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'
import '/src/styles/MovieGrid.css'

// Local movies
const movies = ref([
  {
    title: 'Batman Returns',
    description: 'Batman faces the Penguin and Catwoman in Gotham City.',
    image: new URL('/src/assets/Images/Batman.jpg', import.meta.url).href
  },
  {
    title: 'Wild Wild West',
    description: 'A sci-fi Western with gadgets and action.',
    image: new URL('/src/assets/Images/WildWest.jpg', import.meta.url).href
  }
])

const searchQuery = ref('')

// TMDB Bearer Token
const bearerToken =
  'eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiI1NGY1MzkxOGQ4Yjk4NzVmOTkwMjJmNTYzMDc1MzVlOCIsIm5iZiI6MTc0OTc0ODE5OC4wLCJzdWIiOiI2ODRiMDllNTkwNTQzNmYxYWUzZGVkNzYiLCJzY29wZXMiOlsiYXBpX3JlYWQiXSwidmVyc2lvbiI6MX0.VoSvFJjkSAZPyigBQnVA38cVFH-2gjIga9O6tAzqBVg'

// Search and add movie from TMDB
async function searchMovies() {
  if (!searchQuery.value.trim()) return

  try {
    const response = await axios.get('https://api.themoviedb.org/3/search/movie', {
      params: { query: searchQuery.value },
      headers: {
        accept: 'application/json',
        Authorization: `Bearer ${bearerToken}`
      }
    })

    const movie = response.data.results[0]
    if (movie) {
      movies.value.push({
        id: movie.id,
        title: movie.title,
        description: movie.overview || 'No description available.',
        image: movie.poster_path
          ? `https://image.tmdb.org/t/p/w500${movie.poster_path}`
          : '/src/assets/Images/placeholder.jpg'
      })
      searchQuery.value = ''
    } else {
      alert('No movie found with that title.')
    }
  } catch (err) {
    console.error('Error fetching from TMDB:', err)
    alert('Could not fetch movie. Try again later.')
  }
}

// Remove movie from grid
function removeMovie(index) {
  movies.value.splice(index, 1)
}
</script>

<style scoped>
</style>
