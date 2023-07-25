<template>
  <v-app>
    <v-app-bar app>
      <nuxt-link to="/">
        <img src="@/assets/images/frontend.png" :width="200" aspect-ratio="16/9" class="ml-10 mt-2">
      </nuxt-link>
      <v-spacer></v-spacer>
      <nuxt-link class="menuItems" id="homeButton" to="/">Home</nuxt-link>
      <span class="ml-15"></span>
      <nuxt-link class="menuItems" id="aboutButton" to="/about">About</nuxt-link>
      <span class="ml-15"></span>
      <nuxt-link class="menuItems" id="portfolioButton" to="/portfolio">Portfolio</nuxt-link>
      <span class="ml-15"></span>
      <nuxt-link class="menuItems" id="certificatesButton" to="/certificates">Certificates</nuxt-link>
      <span class="ml-15"></span>
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
  mounted() {
    const buttons = document.querySelectorAll('.menuItems');

    buttons.forEach((button) => {
      button.addEventListener('click', function() {
        buttons.forEach((btn) => btn.classList.remove('clicked'));
        this.classList.add('clicked');
      });
    });
  },
};
</script>


<style scoped>
.menuItems {
  color: black;
  text-decoration: none;
}
.menuItems:hover,
.menuItems.clicked {
  color: grey;
}
</style>
