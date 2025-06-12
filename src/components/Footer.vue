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
export default {
  data() {
    return {
      currentYear: new Date().getFullYear()
    };
  }
};
</script>

<style scoped>
.footer {
  background-color: #111;
  color: #fff;
  padding: 40px 20px;
  font-family: 'Open Sans', 'Gotham', Arial, sans-serif;
}

.footer-top {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-bottom: 30px;
  margin: 0 auto 30px;
}

.footer-left {
  margin-bottom: 25px;
}

.footer-title {
  font-size: 24px;
  font-weight: 600;
  margin-bottom: 15px;
  letter-spacing: 0.5px;
}

.footer-address {
  line-height: 1.6;
  font-size: 16px;
  color: rgba(255, 255, 255, 0.8);
}

.footer-right {
  display: flex;
  align-items: center;
  gap: 20px;
}

.follow-text {
  font-size: 16px;
  color: rgba(255, 255, 255, 0.8);
  margin: 0;
}

.social-icons {
  display: flex;
  gap: 20px;
}

.social-icon {
  width: 28px;
  height: 28px;
  transition: transform 0.3s ease, opacity 0.3s;
}

.social-icon:hover {
  opacity: 0.8;
  transform: translateY(-2px);
}

.footer-bottom {
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  padding-top: 20px;
  display: flex;
  flex-direction: column;
  gap: 15px;
  margin: 0 auto;
  font-size: 14px;
  color: rgba(255, 255, 255, 0.6);
}

.copyright, .credits {
  margin: 0;
}

@media (min-width: 768px) {
  .footer {
    padding: 50px 40px;
  }
  
  .footer-top {
    flex-direction: row;
    align-items: flex-start;
  }
  
  .footer-left {
    margin-bottom: 0;
  }
  
  .footer-title {
    font-size: 28px;
  }
  
  .footer-bottom {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    padding-top: 25px;
  }
}

@media (min-width: 1024px) {
  .footer {
    padding: 60px 80px;
  }
  
  .footer-title {
    font-size: 32px;
  }
  
  .footer-address {
    font-size: 17px;
  }
  
  .follow-text {
    font-size: 17px;
  }
  
  .footer-bottom {
    font-size: 15px;
  }
}
</style>