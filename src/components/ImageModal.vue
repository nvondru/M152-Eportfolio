<template>
  <div class="imageModal" @click="closeImageModal">
    <div class="image__container">
      <img class="image--processed" :src="resolveImgUrl(imgName)" alt />
      <img class="image--original" :src="resolveImgUrl(imgName + 'Original')" alt />
    </div>
  </div>
</template>

<script>
export default {
  name: "ImageModal",
  props: ["imgName"],
  methods: {
    closeImageModal() {
      this.$emit("closeImageModal");
    },
    resolveImgUrl(imgName) {
      var images = require.context("../assets/", false, /\.jpg$/);
      return images("./" + imgName + ".jpg");
    }
  }
};
</script>

<style scoped>
.imageModal {
  position: absolute;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: #000000c2;
  z-index: 2000;
}
img {
  width: 100%;
  margin: 0px;
  padding: 0px;
  display: block;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}

.image--original {
  position: absolute;
  transform: translateY(-100%);
  animation: revealImage 4s infinite 1s;
}

.image__container {
  position: relative;
  top: 50%;
  transform: translate(0%, -50%);
}

@keyframes revealImage {
  0% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>