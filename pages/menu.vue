<template>
  <v-layout>
    <v-flex>
      <main>
        <!-- Hero Section -->
        <section id="menu-page">
          <h1>Menu Page</h1>
        </section>
      </main>
    </v-flex>
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
