<template>
  <img :src="src" :alt="alt" :style="inlineStyle" @load="onLoad" />
</template>

<script>
export default {
  props: {
    src: {
      type: String,
      required: true,
    },
    alt: {
      type: String,
      default: '',
    },
    inlineStyle: {
      type: Object,
      default: () => ({}),
    },
    formats: {
      type: Array,
      default: () => [],
    },
  },
  computed: {
    webpSrc() {
      if (this.formats.includes('webp')) {
        const webpSrc = this.src.replace(/\.[^.]+$/, '.webp');
        return this.$nuxt.$img.resolve(webpSrc);
      }
      return null;
    },
  },
  methods: {
    onLoad(event) {
      event.target.style.opacity = 1;
    },
  },
};
</script>
