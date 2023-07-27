<template>
  <v-card
    class="mx-auto text-center mt-5"
    :style="{ backgroundImage: 'url(' + require('@/assets/images/background.png') + ')', height: '80vh', position: 'relative' }"
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
  </v-card>
</template>

<script>
export default{
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
  bottom: 70px; /* Adjust this value as needed */
  right: 40px; /* Adjust this value as needed */
}

/* Add responsive styles to adjust button position on smaller screens */
@media (max-width: 600px) {
  .fixed-button-container {
    bottom: 170px;
    right: 20px;
  }
}
</style>
