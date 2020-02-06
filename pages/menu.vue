<template>
  <v-layout>
    <v-row>
      <v-col>
        <main>
          <!-- Hero Section -->
          <section id="menu-page">
            <h1>Menu</h1>
            <v-card>
              <v-tabs v-model="tab" background-color="primary" dark>
                <v-tab v-for="item in items" :key="item.tab">{{ item.tab }}</v-tab>
              </v-tabs>

              <v-tabs-items v-model="tab">
                <v-tab-item v-for="item in items" :key="item.tab">
                  <v-card flat>
                    <v-card-text>{{ item.content }}</v-card-text>
                  </v-card>
                </v-tab-item>
              </v-tabs-items>
            </v-card>
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
  },
  data() {
    return {
      tab: null,
      items: [
        { tab: 'Starters', content: 'Tab 1 Content' },
        { tab: 'Drinks', content: 'Tab 2 Content' },
        { tab: 'Entrees', content: 'Tab 3 Content' },
        { tab: 'Ala-carte', content: 'Tab 4 Content' }
      ]
    }
  }
}
</script>

<style lang="scss">
</style>
