<template>
  <v-app>
    <!-- Header Area -->
    <v-navigation-drawer
      id="main-nav"
      v-model="mainNav"
      :mini-variant="miniVariant"
      dark
      fixed
      left
      :width="navWidth"
    >
      <v-toolbar-title>{{ formattedAppTitle }}</v-toolbar-title>
      <v-app-bar-nav-icon class="hidden-md-and-up" @click.stop="drawer = !drawer" />
      <MenuLinks :general-links="generalLinks" list-class="hidden-sm-and-down" />
    </v-navigation-drawer>
    <!-- side/mobile navigation -->
    <v-navigation-drawer v-model="drawer" :mini-variant="miniVariant" dark fixed right>
      <MenuLinks :general-links="generalLinks" list-class="mobile" />
    </v-navigation-drawer>
    <!-- Nuxt content -->
    <v-content>
      <nuxt />
    </v-content>
    <!-- Footer Area -->
    <v-footer dark class="py-6">
      <h2>{{ formattedAppTitle }}</h2>
      <p>{{ appDescription }}</p>
      <ul>
        <li v-for="(link, i) in generalLinks" :key="i + link.title + 'footer'">
          <v-btn text rounded>{{ link.title }}</v-btn>
        </li>
      </ul>
      <v-container>
        {{ new Date().getFullYear() }}&nbsp;-&nbsp;
        <strong>{{ appTitle }}</strong>
      </v-container>
    </v-footer>
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
      let width = '40vw'
      switch (this.$vuetify.breakpoint.name) {
        case 'xs':
          width = '40vw'
          break
        case 'sm':
          width = '35vw'
          break
        case 'md':
          width = '25vw'
          break
        case 'lg':
          width = '20vw'
          break
        case 'xl':
          width = '20vw'
          break
      }
      return width
    }
  }
}
</script>

<style lang="scss">
// global styles shared among pages can go here

// global

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html {
  font-family: 'Open Sans', sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

html,
body {
  min-height: 100vh;
  overflow-x: hidden;
}

.v-card__title {
  word-break: break-word;
}

// main nav
#main-nav {
  background-color: rgba(0, 0, 0, 0.5);
  .v-navigation-drawer__content {
    display: flex;
    flex-direction: column;
    justify-content: center;
    position: relative;
    .v-toolbar__title {
      color: #fff;
      font-family: 'Playfair Display', serif;
      font-size: 2rem;
      font-weight: 900;
      position: relative;
      text-align: center;
      top: -15vh;
    }

    .v-app-bar__nav-icon {
      align-self: center;
      position: relative;
      top: -10vh;
      .v-btn__content i {
        font-size: 4rem;
      }
    }

    .v-list {
      background: none;
      display: flex;
      flex-direction: column;
      margin: 0 2rem;

      .v-list-item {
        flex: 0;
        margin: 0 0.5rem;
        padding: 0 1.5rem;

        .v-list-item__title {
          font-size: 1.33rem;
          font-weight: 400;
        }
      }
    }
  }
}

// footer
.v-footer {
  display: flex;
  flex-direction: column;
  align-items: center;

  ul {
    display: flex;
    justify-content: center;
    list-style-type: none;
    padding: 1rem 0;
  }

  .container {
    display: flex;
    justify-content: center;
    padding: 1rem 0;
  }
}

@media screen and (min-width: 768px) {
  // main nav
  #main-nav {
    .v-navigation-drawer__content {
      .v-toolbar__title {
        font-size: 2rem;
        top: -15vh;
      }
    }
  }
}
</style>