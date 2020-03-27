<template>
  <v-container class="pa-0" fluid>
    <v-row>
      <v-col class="py-0">
        <v-container class="py-0 px-3" fluid>
          <v-container class="mt-6">
            <h1
              :class="{'display-2 pt-3 pb-6': $breakpoint.mdAndUp, 'display-1 pt-3 pb-6': $breakpoint.smAndDown}"
            >Blog</h1>
            <h2
              :class="{'headline mb-0 text-grey': $breakpoint.mdAndUp, 'title mb-0 text-grey': $breakpoint.smAndDown}"
            >A collection of our latest stories</h2>
          </v-container>
          <v-container>
            <v-row>
              <v-col v-for="(blogPost, index) in blogPosts" :key="index" md="6">
                <v-card class="d-flex flex-column" flat height="100%">
                  <v-img
                    src="https://picsum.photos/300/240"
                    lazy-src="https://picsum.photos/10/6"
                    max-height="200px"
                  />
                  <v-card-title class="display-1">{{blogPost.title.substring(0, 70)}}</v-card-title>
                  <v-card-subtitle class="subtitle-1">{{blogPost.description.substring(0, 80)}}</v-card-subtitle>
                  <v-card-text v-html="$md.render(blogPost.body).substring(0, 144) + '...'"></v-card-text>
                  <v-btn
                    class="mt-auto ml-3 mb-6"
                    max-width="120px"
                    color="primary"
                    nuxt
                    :to="`blog/${blogPost.slug}`"
                  >Read more...</v-btn>
                </v-card>
              </v-col>
            </v-row>
          </v-container>
        </v-container>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
export default {
  computed: {
    blogPosts() {
      return this.$store.state.blogPosts
    }
  }
}
</script>
<style lang="scss">
</style>