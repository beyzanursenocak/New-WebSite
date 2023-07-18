<template>
  <v-app>
    <v-app-bar
      app
    >
    <v-row>
      <v-col cols="2">
      <img src="@/assets/images/frontend.png" :width="174" aspect-ratio="16/9" class="ml-10 mt-10">
    </v-col>
    <v-col cols="10" class="text-end pr-15 mt-13">
      <nuxt-link class="menuItems" to="/">Home</nuxt-link>
      <span class="ml-15"></span>
      <nuxt-link class="menuItems" to="/about">About</nuxt-link>
      <span class="ml-15"></span>
      <nuxt-link class="menuItems" to="/portfolio">Portfolio</nuxt-link>
      <span class="ml-15"></span>
      <nuxt-link class="menuItems" to="/certificates">Certificates</nuxt-link>
      <span class="ml-15"></span>
      <nuxt-link class="menuItems" to="/contact">Contact</nuxt-link>
      </v-col>
    </v-row>
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

