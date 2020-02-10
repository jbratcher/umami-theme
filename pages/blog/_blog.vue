<template>
  <v-layout>
    <v-row>
      <v-col :class="columnPadding">
        <main>
          <v-sheet class="ma-0" color="#1E1E1E" dark tile>
            <h1 class="headline px-2 py-4 text-grey">{{ blogPost.title }}</h1>
          </v-sheet>
          <article>
            <v-card class="d-flex flex-column align-center mx-auto" tile>
              <v-img src="https://picsum.photos/800/300" lazy-src="https://picsum.photos/10/6" />
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
  },
  computed: {
    columnPadding() {
      let classes = 'py-0 pl-4'
      switch (this.$vuetify.breakpoint.name) {
        case 'xs':
          classes = 'py-0'
          break
        case 'sm':
        case 'md':
        case 'lg':
        case 'xl':
          classes = 'py-0 pl-4'
          break
      }
      return classes
    }
  }
}
</script>
<style lang="scss" scoped>
.v-card__subtitle + .v-card__text {
  padding-top: 1rem;
}

article {
  .v-image {
    max-width: 100vw;
    max-height: 300px;
  }

  .post-content {
    padding: 1rem 1.5rem;
    width: 95vw;
  }

  .v-card__text {
    font-size: 1rem;
    line-height: 1.5;
  }
}

@media screen and (min-width: 768px) {
  article {
    .v-image {
      width: 100%;
    }
    .post-content {
      padding: 1rem 1.5rem;
      width: 70vw;
    }
    .v-card__text {
      font-size: 1rem;
      line-height: 1.5;
    }
  }
}
</style>