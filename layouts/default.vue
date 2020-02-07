<template>
  <v-app>
    <!-- Header Area -->
    <!-- Large Screen Main Nav -->
    <v-navigation-drawer class="hidden-sm-and-down" id="main-nav" :width="navWidth" left fixed>
      <v-toolbar-title>{{ formattedAppTitle }}</v-toolbar-title>
      <MenuLinks :general-links="generalLinks" />
    </v-navigation-drawer>
    <!-- Small Screen Main Nav -->
    <v-app-bar class="hidden-md-and-up" id="mobile-nav" width="100%">
      <v-toolbar-title>{{ formattedAppTitle }}</v-toolbar-title>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
    </v-app-bar>
    <!-- side/mobile navigation -->
    <v-navigation-drawer v-model="drawer" :mini-variant="miniVariant" color="#121212" fixed right>
      <MenuLinks :general-links="generalLinks" list-class="mobile" />
    </v-navigation-drawer>
    <!-- Nuxt content -->
    <v-content>
      <nuxt />
    </v-content>
    <!-- Footer Area -->
    <v-footer padless tile>
      <section class="content-container py-6" color="#272727">
        <h2>{{ formattedAppTitle }}</h2>
        <p>{{ appDescription }}</p>
      </section>
      <ul>
        <li v-for="(link, i) in generalLinks" :key="i + link.title + 'footer'">
          <v-btn :href="link.to" text rounded>{{ link.title }}</v-btn>
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
  overflow-x: hidden;
}

.v-application--wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 0;
}

.v-content {
  grid-area: main-content;
}

.theme--dark.v-sheet {
  background-color: #121212;
}

.v-card__title {
  word-break: break-word;
}

.heading {
  margin-left: 1rem;
}

// main nav
#main-nav {
  background-color: rgba(0, 0, 0, 0.5);
  grid-area: main-nav;
  padding: 0 1rem;
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
      top: -10vh;
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
      align-items: center;

      .v-list-item {
        flex: 0;
        margin: 0.5rem 0;
        padding: 0 1.5rem;
        min-width: 150px;

        .v-list-item__title {
          font-size: 1.33rem;
          font-weight: 400;
        }
      }

      .v-list-item--active {
        background: #d32f2f; // red darken-2;
        color: #d32f2f; // red darken-2;
        & > * {
          background: none;
          color: #fff;
        }
      }
    }
  }
}

// mobile nav

#mobile-nav {
  z-index: 1;
  .v-toolbar__content {
    display: flex;
    justify-content: space-between;
    .v-toolbar__title {
      font-family: 'Playfair Display', serif;
    }
  }
}

// footer
.v-footer {
  border-top: 1px solid #aaa;
  display: flex;
  flex-direction: column;
  align-items: center;
  grid-area: footer;
  text-align: center;
  width: 100%;

  ul {
    display: flex;
    flex-direction: column;
    align-items: center;
    list-style-type: none;
    padding: 1rem 0;
  }

  .container {
    display: flex;
    justify-content: center;
    padding: 1rem 0;
  }
}

// pages

.content-container {
  h2 {
    font-family: 'Playfair Display', serif;
  }
}

@media screen and (min-width: 960px) {
  .v-application--wrap {
    display: grid;
    grid-template-columns: 1fr 3fr;
    grid-template-areas:
      'main-nav main-content'
      'main-nav footer';
    gap: 0;
  }
  // main nav
  #main-nav {
    .v-navigation-drawer__content {
      .v-toolbar__title {
        font-size: 2rem;
        top: -15vh;
      }
    }
  }

  .v-footer {
    ul {
      flex-direction: row;
      justify-content: center;
    }
  }
}
</style>