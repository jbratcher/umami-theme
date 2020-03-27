<template>
  <v-container class="py-0" fluid>
    <v-row>
      <v-col class="px-0">
        <!-- Main Section -->
        <v-container class="px-0">
          <h1
            :class="{'display-2 font-weight-bold mb-12 mt-6 pl-6': $breakpoint.mdAndUp, 'display-1 font-weight-bold mb-6 mt-0 pl-6': $breakpoint.smAndDown}"
          >Menu</h1>
          <v-card>
            <v-tabs
              v-model="tab"
              color="primary"
              fixed-tabs
              :grow="!$breakpoint.mdAndUp"
              :vertical="!$breakpoint.mdAndUp"
              background-color="primary"
            >
              <v-tab v-for="item in items" :key="item.tab" class="mx-0">{{ item.tab }}</v-tab>
            </v-tabs>

            <v-tabs-items v-model="tab">
              <v-tab-item v-for="item in items" :key="item.tab">
                <v-container>
                  <v-row>
                    <v-col
                      v-for="(entry, i) in item.content"
                      :key="entry.name + i"
                      sm="6"
                      class="py-6"
                    >
                      <v-card class="d-flex" flat>
                        <v-card-title class="pt-0">{{ entry.name }}</v-card-title>
                        <v-card-subtitle class="align-self-center pt-3 title">{{ entry.price }}</v-card-subtitle>
                      </v-card>
                      <v-card flat>
                        <v-card-text class="menu-item-description">{{ entry.description }}</v-card-text>
                      </v-card>
                    </v-col>
                  </v-row>
                </v-container>
              </v-tab-item>
            </v-tabs-items>
          </v-card>
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
</style>
