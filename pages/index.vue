<template>
  <v-layout>
    <v-row>
      <v-col>
        <main>
          <!-- Hero Section -->
          <section id="hero">
            <video autoplay muted loop id="hero-video">
              <source src="/videos/hero.webm" type="video/webm" />
              <source src="/videos/hero.mp4" type="video/mp4" />
            </video>
          </section>
        </main>
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
main {
  #hero {
    min-height: 100vh;
    #hero-video {
      position: fixed;
      right: 0;
      top: 0;
      min-width: 100%;
      min-height: 100%;
    }
  }
}
</style>
