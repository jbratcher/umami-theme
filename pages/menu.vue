<template>
  <v-layout>
    <v-row>
      <v-col>
        <main>
          <!-- Hero Section -->
          <section id="menu-page">
            <h1>Menu Page</h1>
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
</style>
