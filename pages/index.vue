<template>
  <v-card
    class="mx-auto text-center mt-5" style="background-color: #d6ddd6;"
   
  >
  <v-card>
  <div style="background-color: #d6ddd6; font-size: 60px; font-family: 'Dancing Script', cursive; max-height: 700px; margin-bottom: 15px;">Her Şey Bir Kodla Başlar</div>

</v-card>
  <v-container fluid>
        <v-row dense>
          <v-col
            v-for="cardTitle in cardTitles" :key="cardTitle.id"
            :title="cardTitle.title"
            :icon="cardTitle.icon"
            cols="12"
            md="4"
          >
              <img
                :src="require(`@/assets/images/cardTitle/${cardTitle.src}`)"
                :alt="cardTitle.title"
                class="img"
                preload
                loading="lazy"
                sizes="sm:100vw md:50vw lg:400px"
                layout="responsive"
                @click="goPage(cardTitle.link)"
              >
          </v-col>
        </v-row>
      </v-container>
    </v-card>
  </template>

<script>

export default {
  
  data: () => ({
    cardTitles: [
      { title: 'About', src: 'About.png', link: '/about', flex: 4 },
      { title: 'Food Blog', src: 'Certificates.png', link: '/portfolio' , flex: 4 },
      { title: 'CarTrader', src: 'Portfolio.png', link: '/certificates' , flex: 4 },
    ],
  }),
  methods: {
    goPage: function (link) {
      window.open(link);
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Dancing+Script&display=swap');

.img {
  width: 100%;
  height: 250px;
  object-fit: cover;
  cursor: pointer;
}
</style>

