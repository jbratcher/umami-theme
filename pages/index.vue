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
              <v-btn color="primary" rounded>
                <a href="/contact">Reservations</a>
              </v-btn>
            </li>
          </ul>

          <section class="content-container">
            <h1>Umami</h1>
            <h2>We deliver deliciousness</h2>
          </section>

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
  .content-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    z-index: 1;
    top: 10vh;
    text-align: center;

    h1 {
      color: #d32f2f;
      font-size: 5rem;
      text-shadow: 0.25rem 0.25rem 0.5rem #111;
    }

    h2 {
      font-size: 2rem;
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

@media screen and (min-width: 960px) {
  #hero {
    .content-container {
      top: 10vh;

      h1 {
        font-size: 8rem;
        text-shadow: 0.25rem 0.25rem 0.5rem #111;
      }

      h2 {
        font-size: 2rem;
      }
    }
  }
}
</style>
