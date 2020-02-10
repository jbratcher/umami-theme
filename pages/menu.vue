<template>
  <v-layout>
    <v-row>
      <v-col class="pb-0 pt-3">
        <main>
          <!-- Hero Section -->
          <section id="menu-page">
            <h1 class="heading">Menu</h1>
            <v-card>
              <v-tabs
                v-model="tab"
                color="primary"
                fixed-tabs
                hide-slider
                :vertical="menuDirection"
              >
                <v-tab v-for="item in items" :key="item.tab" class="mx-0">{{ item.tab }}</v-tab>
              </v-tabs>

              <v-tabs-items v-model="tab">
                <v-tab-item v-for="item in items" :key="item.tab">
                  <v-card class="menu-items" flat>
                    <v-container
                      v-for="(entry, i) in item.content"
                      :key="entry.name + i"
                      class="menu-item"
                    >
                      <span class="menu-item-title">{{ entry.name }}</span>
                      <span class="menu-item-price">{{ entry.price }}</span>
                      <span class="menu-item-description">{{ entry.description }}</span>
                    </v-container>
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
      starters: [
        {
          name: 'Avacado Toast',
          description: 'Fresh Haas avacado, toast, herb butter',
          price: '9'
        },
        {
          name: 'Harvest Nachos',
          description:
            'Blue corn tortilla chips, goat cheese, garbanzo beans, salsa fresca',
          price: '12'
        },
        {
          name: 'Flatbread mini pizza',
          description: 'A crispy cracker crust with up to 3 toppings',
          price: '8'
        }
      ],
      drinks: [
        {
          name: 'House Lemonade',
          description: 'A delicious fresh squeezed in house refresher',
          price: '3'
        },
        {
          name: 'Soda',
          description: 'Choose from a variety of fountain drinks on tap',
          price: '2'
        },
        {
          name: 'Power water',
          description: 'More than just water',
          price: '5'
        }
      ],
      entrees: [
        {
          name: 'Huevos Rancheros',
          description: 'A classic dish serving the masses',
          price: '25'
        },
        {
          name: 'Surf & Turf',
          description: 'Steak and lobster but with a fun name',
          price: '45'
        },
        {
          name: 'Vegan Delight',
          description: "For those who don't eat meat",
          price: '30'
        }
      ],
      alacarte: [
        {
          name: 'Rice',
          description: 'White, brown, or basmati steamed rice',
          price: '1'
        },
        {
          name: 'Egg',
          description: 'Your choice of scrambled, fried, or poached',
          price: '1'
        },
        {
          name: 'Biscuit',
          description: 'A homemade buttermilk biscuit',
          price: '1'
        }
      ]
    }
  },
  computed: {
    items() {
      return [
        { tab: 'Starters', content: this.starters },
        { tab: 'Drinks', content: this.drinks },
        { tab: 'Entrees', content: this.entrees },
        { tab: 'Ala-carte', content: this.alacarte }
      ]
    },
    menuDirection() {
      let vertical = true
      switch (this.$vuetify.breakpoint.name) {
        case 'xs':
          vertical = true
          break
        case 'sm':
        case 'md':
        case 'lg':
        case 'xl':
          vertical = false
          break
      }
      return vertical
    }
  }
}
</script>

<style lang="scss">
.v-slide-group__content {
  align-items: center;
  max-width: 100vw;
  .v-tab {
    font-size: 1.5rem;
  }
}
.v-card.menu-items {
  display: flex;
  flex-direction: column;
  padding: 1rem;
}

.menu-item {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-auto-rows: 1fr;
  grid-template-areas:
    'title price'
    'description description';
  margin: 1rem 0;
  .menu-item-title {
    font-size: 1.5rem;
    font-weight: 700;
    grid-area: title;
  }

  .menu-item-price {
    font-size: 1.33rem;
    font-weight: 200;
    grid-area: price;
    justify-self: end;
    margin-right: 4rem;
  }

  .menu-item-description {
    align-self: start;
    font-size: 1.125rem;
    grid-area: description;
    margin-right: 1rem;
  }
}

@media screen and (min-width: 960px) {
  .v-card.menu-items {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-auto-rows: 1fr;
  }

  .menu-item {
    margin: 1rem 0;
    .menu-item-title {
      font-size: 1.5rem;
    }

    .menu-item-price {
      font-size: 1.33rem;
      justify-self: end;
      margin-right: 4rem;
    }

    .menu-item-description {
      align-self: start;
      font-size: 1.125rem;
      margin-right: 1rem;
    }
  }
}
</style>
