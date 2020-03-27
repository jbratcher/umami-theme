<template>
  <v-container class="pa-0" fluid>
    <v-row>
      <v-col class="py-0">
        <v-container class="pa-0" fluid>
          <article>
            <v-card class="d-flex flex-column mx-auto text-center" tile>
              <v-img
                :alt="blogPost.title"
                :aspect-ratio="16/9"
                src="https://picsum.photos/800/300"
                lazy-src="https://picsum.photos/10/6"
                :height="$breakpoint.mdAndUp ? '18.75rem' : '12.5rem'"
              />
              <v-card-title
                :class="{'display-2 mx-auto pt-6 pb-9': $breakpoint.mdAndUp, 'display-1  mx-auto pt-6  pb-9': $breakpoint.smAndDown}"
              >{{blogPost.title}}</v-card-title>
              <v-card-subtitle
                :class="{'headline font-weight-regular pb-9': $breakpoint.mdAndUp, 'title font-weight-regular pb-9': $breakpoint.smAndDown}"
              >{{blogPost.description}}</v-card-subtitle>
              <v-card class="mx-auto text-left" flat :width="$breakpoint.mdAndUp ? '80%' : '90vw'">
                <v-card-text class="body-1" v-html="$md.render(blogPost.body)"></v-card-text>
              </v-card>
            </v-card>
          </article>
        </v-container>
      </v-col>
    </v-row>
  </v-container>
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
</style>