<template>
  <v-app>
    <!-- Header Area -->
    <!-- Large Screen Main Nav -->
    <v-container class="py-0" fluid>
      <v-row>
        <v-col class="pa-0">
          <video autoplay muted loop id="hero-video">
            <source src="/videos/hero.mp4" type="video/mp4" />
            <source src="/videos/hero.webm" type="video/webm" />
          </video>
        </v-col>
      </v-row>
      <v-row>
        <v-col col="4" sm="12">
          <v-navigation-drawer
            class="hidden-sm-and-down align-center"
            color="rgba(0, 0, 0, 0.5)"
            :width="navWidth"
            left
            app
          >
            <v-toolbar-title class="display-2 my-12 pb-12 text-center">{{ formattedAppTitle }}</v-toolbar-title>
            <MenuLinks :general-links="generalLinks" />
          </v-navigation-drawer>
          <!-- Small Screen Main Nav -->
          <v-app-bar class="hidden-md-and-up justify-space-around" width="100%">
            <v-toolbar-title class="display-1">{{ formattedAppTitle }}</v-toolbar-title>
            <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
          </v-app-bar>
          <!-- side/mobile navigation -->
          <v-navigation-drawer
            v-model="drawer"
            :mini-variant="miniVariant"
            color="grey darken-4"
            fixed
            right
          >
            <MenuLinks :general-links="generalLinks" />
          </v-navigation-drawer>
        </v-col>
      </v-row>
      <!-- Nuxt content -->
      <v-row>
        <v-col cols="9" class="pa-0 ml-auto">
          <v-content class="pa-0">
            <nuxt />
          </v-content>
        </v-col>
      </v-row>
      <!-- Footer Area -->
      <v-row>
        <v-col cols="9" class="pa-0 mt-12 ml-auto">
          <v-footer class="d-flex flex-column align-center text-center" tile>
            <v-container class="py-6" color="grey darken-4">
              <h2>{{ formattedAppTitle }}</h2>
              <p>{{ appDescription }}</p>
            </v-container>
            <nav>
              <ul>
                <li v-for="(link, i) in generalLinks" :key="i + link.title + 'footer'">
                  <v-btn :href="link.to" text rounded>{{ link.title }}</v-btn>
                </li>
              </ul>
            </nav>
            <v-container>
              {{ new Date().getFullYear() }}&nbsp;-&nbsp;
              <strong>{{ appTitle }}</strong>
            </v-container>
          </v-footer>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
import MenuLinks from '../components/MenuLinks.vue'

export default {
  components: {
    MenuLinks
  },
  data() {
    return {
      appTitle: process.env.title,
      appDescription: process.env.description,
      drawer: false,
      // add main nav links here
      // material design icons https://materialdesignicons.com/
      generalLinks: [
        {
          icon: 'mdi-home',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-hamburger',
          title: 'Menu',
          to: '/menu'
        },
        {
          icon: 'mdi-silverware',
          title: 'About',
          to: '/about'
        },
        {
          icon: 'mdi-post',
          title: 'Blog',
          to: '/blog'
        },
        {
          icon: 'mdi-email',
          title: 'Contact',
          to: '/contact'
        }
      ],
      mainNav: true,
      miniVariant: false
    }
  },
  computed: {
    formattedAppTitle() {
      if (this.appTitle.length > 10) {
        return this.appTitle.substring(0, 10) + '...'
      } else {
        return this.appTitle
      }
    },
    navWidth() {
      let width = '25vw'
      switch (this.$vuetify.breakpoint.name) {
        case 'xs':
          width = '25vw'
          break
        case 'sm':
          width = '25vw'
          break
        case 'md':
          width = '25vw'
          break
        case 'lg':
          width = '25vw'
          break
        case 'xl':
          width = '25vw'
          break
      }
      return width
    }
  }
}
</script>

<style lang="scss">
// global

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html,
body,
.v-application {
  font-family: 'Open Sans', sans-serif;
  font-size: 16px;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  line-height: 1.5;
  box-sizing: border-box;
  min-height: 100vh;
  overflow-x: hidden;
  scroll-behavior: smooth;
  text-rendering: optimizeSpeed;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  word-break: break-word;
  word-spacing: 1px;
}

// main nav

.v-toolbar,
.v-toolbar--prominent {
  .v-toolbar__content {
    align-items: center;
    padding: 0.25rem 0.75rem;
  }
}

// global styles shared among pages can go here

.v-application {
  .v-card__title,
  .v-card__subtitle,
  .v-card__text {
    word-break: keep-all;
  }

  article > * + * {
    margin-top: 1em;
  }

  nav > ul {
    padding-left: 0;
  }

  ul,
  ol {
    list-style-type: none;
  }

  a {
    text-decoration: none;
  }
}

/* Remove all animations and transitions for people that prefer not to see them */
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}

// full screen video

#hero-video {
  position: fixed;
  right: 0;
  top: 0;
  min-width: 100%;
  min-height: 100%;
}
</style>