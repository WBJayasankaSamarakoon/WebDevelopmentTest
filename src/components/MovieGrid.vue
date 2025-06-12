<template>
  <div class="movie-grid">
    <div class="header-container">
      <h2>Collect your favourites</h2>
      <div class="search-bar">
        <div class="search-wrapper">
          <img src="/src/assets/Icons/SearchWhite.svg" alt="Search" class="search-icon" />
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
import { ref } from 'vue'
import axios from 'axios'

const movies = ref([
  {
    title: 'Batman Returns',
    description: 'Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut…',
    image: new URL('/src/assets/Images/Batman.jpg', import.meta.url).href
  },
  {
    title: 'Wild Wild West',
    description: 'Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut…',
    image: new URL('/src/assets/Images/WildWest.jpg', import.meta.url).href
  },
  {
    title: 'The Amazing Spiderman',
    description: 'Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut…',
    image: new URL('/src/assets/Images/Spiderman.jpg', import.meta.url).href
  }
])

const searchQuery = ref('')

async function searchMovies() {
  if (!searchQuery.value) return

  try {
    const apiKey = 'YOUR_TMDB_API_KEY' // Replace with actual key
    const response = await axios.get('https://api.themoviedb.org/3/search/movie', {
      params: {
        api_key: apiKey,
        query: searchQuery.value
      }
    })

    if (response.data.results.length > 0) {
      const newMovie = response.data.results[0]
      movies.value.push({
        title: newMovie.title,
        description: newMovie.overview || 'No description available.',
        image: `https://image.tmdb.org/t/p/w500${newMovie.poster_path}`
      })
      searchQuery.value = ''
    }
  } catch (err) {
    console.error('Error fetching from TMDB:', err)
  }
}

function removeMovie(index) {
  movies.value.splice(index, 1)
}
</script>

<style scoped>
.movie-grid {
  padding: 2rem;
  color: white;
  background-color: #1f1f1f;
  font-family: 'Open Sans', 'Gotham', Arial, sans-serif;
}

.header-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
  max-width: 1980px;
  margin: 0 auto;
  gap: 3rem;
  padding: 0 2rem;
}

.movie-grid h2 {
  font-size: 1.5rem;
  letter-spacing: 1px;
}

.search-bar {
  width: 30%;
  display: flex;
  justify-content: flex-end;
}

.search-wrapper {
  position: relative;
  width: 95%;
  display: flex;
  justify-content: flex-end;
}

.search-icon {
  position: absolute;
  left: 12px;
  top: 50%;
  transform: translateY(-50%);
  width: 20px;
  height: 20px;
}

.search-wrapper input {
  padding: 0.8rem 1rem 0.8rem 2.5rem;
  width: 95%;
  background: transparent;
  border: 1px solid #555;
  color: white;
  border-radius: 6px;
  outline: none;
  font-size: 1rem; 
}

.movies {
  display: grid;
  grid-template-columns: repeat(3, 1fr); 
  gap: 1.5rem;
}

.movie-card {
  background-color: #2b2b2b;
  border-radius: 6px;
  overflow: hidden;
  width: 100%;
  position: relative;
}

.movie-card img {
  width: 100%;
  height: 400px;
  object-fit: cover;
}

.close-btn {
  position: absolute;
  top: 8px;
  right: 8px;
  background: #2c2c2c;
  border: none;
  color: white;
  padding: 0.8rem 0.9rem;
  font-size: 1.2rem;
  cursor: pointer;
  border-radius: 4px;
}

.movie-info {
  padding: 1rem;
}

.movie-info h3 {
  margin: 0;
  font-size: 1.1rem;
}

.movie-info p {
  font-size: 0.9rem;
  color: #ccc;
  margin-top: 0.5rem;
}

.movies-wrapper {
  max-width: 1980px;
  margin: 0 auto;
  gap: 3rem;
  padding: 0 2rem;
  display: flex;
  justify-content: center;
}

hr {
  border: none;
  height: 1px;
  background-color: #444;
  margin: 1rem auto;
  width: 96%; 

}


</style>