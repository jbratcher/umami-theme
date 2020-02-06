<template>
  <v-layout>
    <v-row>
      <v-col>
        <v-container fluid id="hero">
          <!-- Hero Section -->
          <ul class="cta-links">
            <li>
              <a href="tel:123-456-7890">(123)&nbsp;456-7890</a>
            </li>
            <li>
              <v-btn color="red" rounded>
                <a href="/contact">Reservations</a>
              </v-btn>
            </li>
          </ul>

          <video autoplay muted loop id="hero-video">
            <source src="/videos/hero.mp4" type="video/mp4" />
            <source src="/videos/hero.webm" type="video/webm" />
          </video>
        </v-container>
      </v-col>
    </v-row>
  </v-layout>
</template>

<script>
export default {
  head() {
    return {
      script: [
        { src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }
      ]
    }
  }
}
</script>

<style lang="scss">
#hero {
  min-height: 100vh;
  .cta-links {
    display: flex;
    align-items: center;
    list-style: none;
    justify-content: flex-end;
    position: relative;
    z-index: 1;
    li {
      margin: 0 1rem;
      a {
        color: #fff;
        text-decoration: none;
      }
    }
  }
  #hero-video {
    position: fixed;
    right: 0;
    top: 0;
    min-width: 100%;
    min-height: 100%;
  }
}
</style>
