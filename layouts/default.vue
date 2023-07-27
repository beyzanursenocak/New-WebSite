<template>
  <v-app>
    <v-app-bar app>
      <nuxt-link to="/">
        <img src="@/assets/images/frontend.png" :width="180" aspect-ratio="16/9" class="mt-2">
      </nuxt-link>
      <v-spacer></v-spacer>
      
      <!-- Açılır menüyü buraya ekleyelim -->
      <v-menu v-if="showMenu" offset-y>
        <template v-slot:activator="{ on, attrs }">
          <div v-bind="attrs" v-on="on" class="menuItems" id="menuButton">      
            <v-btn
              color="#5C8D89"
              rounded
              >
                Menu
              </v-btn>
          </div>
        </template>
        <v-list class="menuList">
          <nuxt-link to="/" class="menuItems">
            <v-list-item-title>Home</v-list-item-title>
          </nuxt-link>
          <hr style="background-color: #404940;">
          <nuxt-link to="/about" class="menuItems">
            <v-list-item-title>About</v-list-item-title>
          </nuxt-link>
          <hr style="background-color: #404940;">
          <nuxt-link to="/portfolio" class="menuItems">
            <v-list-item-title>Portfolio</v-list-item-title>
          </nuxt-link>
          <hr style="background-color: #404940;">
          <nuxt-link to="/certificates" class="menuItems">
            <v-list-item-title>Certificates</v-list-item-title>
          </nuxt-link>
          <hr style="background-color: #404940;">
        </v-list>
      </v-menu>

      <span class="ml-5"></span>
      <nuxt-link v-if="!showMenu" class="menuItems" id="homeButton" to="/">Home</nuxt-link>
      <span class="ml-5"></span>
      <nuxt-link v-if="!showMenu" class="menuItems" id="aboutButton" to="/about">About</nuxt-link>
      <span class="ml-5"></span>
      <nuxt-link v-if="!showMenu" class="menuItems" id="portfolioButton" to="/portfolio">Portfolio</nuxt-link>
      <span class="ml-5"></span>
      <nuxt-link v-if="!showMenu" class="menuItems" id="certificatesButton" to="/certificates">Certificates</nuxt-link>
      <span class="ml-5"></span>
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  title: 'Firdes Beyzanur Senocak',
  data() {
    return {
      showMenu: false
    };
  },
  mounted() {
    window.addEventListener('resize', this.checkWindowSize);
    this.checkWindowSize();
  },
  methods: {
    checkWindowSize() {
      this.showMenu = window.innerWidth < 600;
    }
  }
};
</script>

<style scoped>
.menuItems {
  color: black;
  text-decoration: none;
  cursor: pointer;
}

.menuItems:hover,
.menuItems.clicked {
  color: grey;
}

#menuButton {
  cursor: pointer;
}

.menuList {
  min-width: 200px;
  text-align: left;
  background-color: #d6ddd6;
  box-shadow: #d6ddd6;
  border: 1px solid #d6ddd6;
  padding: 8px 0;
}

.menuList a {
  display: block;
  padding: 8px 16px;
  text-align: center;
  color: black;
}

.menuList a:hover {
  background-color: #404940;
}
</style>
