<template>
  <v-card
    class="mx-auto text-center mt-5"
    :style="{ backgroundImage: 'url(' + require('@/assets/images/background.webp') + ')', height: '80vh', position: 'relative' }"
  >
    <div class="centered-text">
      <div style="font-size: 8vw; font-family: 'Dancing Script', cursive;">All Things Starts With A Code</div>
    </div>
    <div class="fixed-button-container">
      <v-btn
        color="#5C8D89"
        rounded
        @click="downloadCV"
      >
      Click Here For My CV
      </v-btn>
    </div>
    <v-container fluid>
      <v-row dense>
        <v-col
          v-for="social in socialMedias" :key="social.id"
          cols="12"
          md="4"
        >
          <a v-if="social.title === 'Mail'" :href="`mailto:${social.link}`">
            <v-card class="mx-auto text-center mt-5" style="height: 300px; width: 300px;">
              <nuxt-img
                :src="require(`@/assets/images/socialMedia/${social.src}`)"
                :alt="social.title"
                preload
                loading="lazy"
                sizes="sm:100vw md:50vw lg:400px"
                layout="responsive"
              ></nuxt-img>
            </v-card>
          </a>
          <a v-else :href="social.link" target="_blank" rel="noopener noreferrer">
            <v-card class="mx-auto text-center mt-5" style="height: 300px; width: 300px;">
              <nuxt-img
                :src="require(`@/assets/images/socialMedia/${social.src}`)"
                :alt="social.title"
                preload
                loading="lazy"
                sizes="sm:100vw md:50vw lg:400px"
                layout="responsive"
              ></nuxt-img>
            </v-card>
          </a>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>


<script>
export default{
  data: () => ({
    socialMedias: [
      { title: 'GitHub', src: 'GitHub.webp', link: 'https://github.com/Firdesbeyzanur' , flex: 4 },
      { title: 'Linkedin', src: 'Linkedin.webp', link: 'https://www.linkedin.com/in/firdesbeyzanursenocak/' , flex: 4 },
      { title: 'Mail', src: 'Mail.webp', link: 'beyzanursenocak96@gmail.com' , flex: 4 }
    ],
  }),

  methods: {
    downloadCV() {
      const link = document.createElement("a");
      link.href = "/CV/firdes-beyzanur-senocak-cv.pdf";
      link.download = "firdes-beyzanur-senocak.pdf";
      link.target = "_blank";
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
    },
  },
}
</script>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Dancing+Script&display=swap');

.centered-text {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.fixed-button-container {
  position: absolute;
  bottom: 70px; 
  right: 40px; 
}

@media (max-width: 600px) {
  .fixed-button-container {
    bottom: 170px;
    right: 20px;
  }
}
</style>
