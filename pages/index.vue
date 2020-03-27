<template>
  <v-container>
    <v-row>
      <v-col class="d-flex flex-column align-center justify-center">
        <!-- Hero Section -->
        <v-container class="mb-12" fluid>
          <ul class="d-flex align-center justify-end">
            <li class="mx-3 mb-3">
              <a
                href="tel:123-456-7890"
                :class="{'display-1': $breakpoint.mdAndUp, 'headline': $breakpoint.smAndDown}"
              >(123)&nbsp;456-7890</a>
            </li>
            <li class="mx-3">
              <v-btn color="primary" rounded>
                <a href="/contact" class="white--text">Reservations</a>
              </v-btn>
            </li>
          </ul>
        </v-container>

        <v-container class="mb-12 pt-7 pb-12 text-center" fluid>
          <h1
            :class="{'display-4 font-weight-bold red--text mb-6': $breakpoint.mdAndUp, 'display-2 font-weight-bold red--text mb-6': $breakpoint.smAndDown}"
          >Umami</h1>
          <h2
            :class="{'display-1 font-weight-bold mb-12 pb-6': $breakpoint.mdAndUp, 'headline font-weight-bold mb-12 pb-6': $breakpoint.smAndDown}"
          >We deliver deliciousness</h2>
        </v-container>
      </v-col>
    </v-row>
  </v-container>
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
