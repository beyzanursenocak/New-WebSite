<template>
  <v-card class="mx-auto" max-width="1000px">
    <nuxt-img
      :src="require('@/assets/images/firdes-beyzanur-senocak.webp')"
      formats="webp,jpeg"
      alt="Firdes Beyzanur Senocak"
      class="img"
      loading="eager"
      sizes="100vw"
      layout="responsive"
    >
    </nuxt-img>
    <v-btn
      color="#154360"
      class="cvButton"
      @click="downloadCV"
    >
      <v-icon>mdi-link-variant</v-icon>
      Click Here For My CV
    </v-btn>
    <v-card-title class="cardTitle">
      Jr. Front-End Developer
    </v-card-title>
    <v-dialog v-model="dialog" width="1000px">
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="#89461F"
          dark
          v-bind="attrs"
          v-on="on"
          class="homebutton"
        >
          More Details
        </v-btn>
      </template>
      <v-card>
        <v-card-title class="text-h5" style="background-color: #4B86B4;">
          Information
        </v-card-title>
        <v-divider></v-divider>
        <v-card-text class="homeText">
          Hello and Welcome!
          <v-spacer></v-spacer>
          I am Firdes Beyzanur Şenocak, and this is my personal website. I share my project contents here.
          <v-spacer></v-spacer>
          Welcome! I am Firdes Beyzanur Şenocak, and this is my personal website where I share content about my projects. I am here to share interesting topics, showcase my projects, and share my experiences with you. I hope you enjoy navigating through my site and feel free to contact me.
          <v-spacer></v-spacer>
          Thank you,
          <v-spacer></v-spacer>
          You can learn more about me by visiting my <nuxt-link to="/about">About Me</nuxt-link> page. There, I provide a brief summary about my life.
          <v-spacer></v-spacer>
          If you would like to review my projects, you can visit my <n-link to="portfolio">Portfolio</n-link> page. There, I showcase some of my own projects and provide detailed information about them.
          <v-spacer></v-spacer>
          If you would like to view my certificates, you can visit my <nuxt-link to="/certificates">Certificates</nuxt-link> page. There, you can find a list and details of various certificates I have earned. This page is a useful resource for those who want to learn more about the trainings I have taken and the skills I have acquired.
        </v-card-text>
        <v-divider></v-divider>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" text @click="dialog = false">
            Oki Doki
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      dialog: false,
    };
  },
  methods: {
    downloadCV() {
      const link = document.createElement("a");
      link.href = "/firdes-beyzanur-senocak-cv.pdf";
      link.download = "firdes-beyzanur-senocak.pdf";
      link.target = "_blank";
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
    },
  },
};
</script>

<style scoped>
.cardTitle {
  font-size: 20px;
}

.homeText {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: large;
}

.homebutton {
  background-color: #000;
  color: #fff;
  padding: 10px 20px;
  position: relative;
}

.cvButton {
  position: relative;
}

.img {
  width: 100%;
  height: auto;
  object-fit: cover;
  margin-bottom: 10px;
}
</style>
