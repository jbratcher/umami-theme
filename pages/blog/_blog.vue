<template>
  <v-layout>
    <v-row>
      <v-col class="py-0 pl-4">
        <main>
          <v-sheet class="ma-0" color="primary" dark tile>
            <h1 class="headline pa-2">Blog > {{ blogPost.title }}</h1>
          </v-sheet>
          <article>
            <v-card class="d-flex flex-column align-center mx-auto" tile>
              <v-img
                src="https://picsum.photos/800/300"
                lazy-src="https://picsum.photos/800/300"
                min-width="100%"
                max-height="300px"
              />
              <v-card-title class="display-1">{{blogPost.title}}</v-card-title>
              <v-card-subtitle class="subtitle-1">{{blogPost.description}}</v-card-subtitle>
              <v-card-text v-html="$md.render(blogPost.body)"></v-card-text>
            </v-card>
          </article>
        </main>
      </v-col>
    </v-row>
  </v-layout>
</template>
<script>
export default {
  async asyncData({ params, payload }) {
    if (payload) return { blogPost: payload }
    else
      return {
        blogPost: await require(`~/assets/content/blog/${params.blog}.json`)
      }
  }
}
</script>
<style lang="scss" scoped>
.col {
  margin: 0;
  padding: 0;
}
</style>