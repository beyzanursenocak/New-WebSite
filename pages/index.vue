<template>
    <v-card class="mt-5 card">
        <div>
            <img class="card" src="@/assets/images/wallpaper.png">
            <p class="custom-font">EXPRESS CREATIVITY THROUGH CODING WITH ME</p>
            <img class="logo" src="@/assets/images/zyro-image.png">
        </div>
        <div class="mt-5 text-center">
            <v-row>
                <v-col cols="4">
                    <nuxt-link class="menuItems" to="/about">About</nuxt-link>
                    <img class="mt-5" src="@/assets/images/aboutme.jpg">
                </v-col>
                <v-col cols="4">
                    <nuxt-link class="menuItems" to="/portfolio">Portfolio</nuxt-link>
                    <img class="mt-5" src="@/assets/images/wallpaper.png">
                </v-col>
                <v-col cols="4">
                    <nuxt-link class="menuItems" to="/certificates">Certificates</nuxt-link>
                    <img class="mt-5" src="@/assets/images/wallpaper.png">
                </v-col>
            </v-row>
        </div>
    </v-card>
</template>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Dancing+Script&display=swap');

.custom-font {
  font-family: 'Dancing Script', cursive;
  font-size: 70px;
  background-color: transparent;
  position: absolute; 
  top: 55%; 
  left: 50%; 
  transform: translate(-50%, -50%); 
  width: 1170px;
    text-align: center;
}
.logo {
  width: 200px;
  background-color: transparent;
  position: absolute; 
  top: 17%; 
  left: 8%; 
  transform: translate(-50%, -50%); 
}
.card{
  position: relative;
  width: 1170px;
  height: 400px;
}
.menuItems{
  color: black;
  text-decoration: none;
}
</style>
