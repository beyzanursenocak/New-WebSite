<template>
  <v-app>
    <v-app-bar
      app
    >
      <img src="@/assets/images/frontend.png" :width="200" aspect-ratio="16/9" class="ml-10 mt-2">
      <v-spacer></v-spacer>
      <nuxt-link class="menuItems" to="/">Home</nuxt-link>
      <span class="ml-15"></span>
      <nuxt-link class="menuItems" to="/about">About</nuxt-link>
      <span class="ml-15"></span>
      <nuxt-link class="menuItems" to="/portfolio">Portfolio</nuxt-link>
      <span class="ml-15"></span>
      <nuxt-link class="menuItems" to="/certificates">Certificates</nuxt-link>
      <span class="ml-15"></span>
      <nuxt-link class="menuItems mr-10" to="/contact">Contact</nuxt-link>
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
      title: 'Firdes Beyzanur Senocak'
    }
</script>

<style scoped>
.menuItems{
  color: black;
  text-decoration: none;
}
</style>

