<template>
  <v-layout>
    <v-row>
      <v-col class="py-0">
        <main>
          <section id="blog-page">
            <h1 class="heading pt-4">Blog</h1>
            <v-sheet color="#1E1E1E" class="ml-1" tile>
              <p class="pl-6 py-3 headline text-grey">A collection of our latest stories</p>
            </v-sheet>
            <v-list class="py-12">
              <v-list-item three-line v-for="(blogPost, index) in blogPosts" :key="index">
                <v-card class="d-flex flex-column align-self-stretch" flat>
                  <v-img
                    src="https://picsum.photos/300/240"
                    lazy-src="https://picsum.photos/10/6"
                    max-height="200px"
                  />
                  <v-card-title class="display-1">{{blogPost.title.substring(0, 70)}}</v-card-title>
                  <v-card-subtitle class="subtitle-1">{{blogPost.description.substring(0, 80)}}</v-card-subtitle>
                  <v-card-text>{{blogPost.body.substring(0, 144) + '...'}}</v-card-text>
                  <v-btn
                    class="mt-auto ml-3 mb-3"
                    max-width="120px"
                    color="primary"
                    nuxt
                    :to="`blog/${blogPost.slug}`"
                  >Read more...</v-btn>
                </v-card>
              </v-list-item>
            </v-list>
          </section>
        </main>
      </v-col>
    </v-row>
  </v-layout>
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
#blog-page {
  .v-list {
    display: flex;
    flex-direction: column;

    .v-list-item {
      margin-bottom: 2rem;
    }
  }
}

@media screen and (min-width: 960px) {
  #blog-page {
    .v-list {
      align-items: stretch;
      display: grid;
      grid-template-columns: 1fr 1fr;
      grid-template-rows: auto;
      gap: 2rem;

      .v-list-item {
        margin-bottom: 0;
      }
    }
  }
}
</style>