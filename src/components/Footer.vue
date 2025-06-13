<template>
  <footer class="footer">
    <div class="footer-top">
      <!-- Left Side: Title and Address -->
      <div class="footer-left">
        <h2 class="footer-title">Amadeus IT Group</h2>
        <p class="footer-address">
          C. Salvador de Madariaga, 1<br />
          28027 Madrid<br />
          Spain
        </p>
      </div>

      <!-- Right Side: Social Icons -->
      <div class="footer-right">
        <p class="follow-text">Follow us on</p>
        <div class="social-icons">
          <a href="https://twitter.com" target="_blank" rel="noopener noreferrer">
            <img src="/src/assets/Icons/TwitterWhite.svg" alt="Twitter" class="social-icon" />
          </a>
          <a href="https://youtube.com" target="_blank" rel="noopener noreferrer">
            <img src="/src/assets/Icons/YoutubeWhite.svg" alt="YouTube" class="social-icon" />
          </a>
        </div>
      </div>
    </div>

    <div class="footer-bottom">
      <!-- Left Side -->
      <p class="copyright">
        Copyright © {{ currentYear }} Amadeus Hotels. All rights reserved.
      </p>

      <!-- Right Side -->
      <p class="credits">
        Photos by Felix Mooneeram & Serge Kutuzov on Unsplash
      </p>
    </div>
  </footer>
</template>

<script>
import '/src/styles/Footer.css'

export default {
  data() {
    return {
      currentYear: new Date().getFullYear()
    };
  }
};
</script>