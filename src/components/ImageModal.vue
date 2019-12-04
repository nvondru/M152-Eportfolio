<template>
  <div class="imageModal">
    <img src="../assets/logo.svg" alt class="closeBtn" @click="closeImageModal" />
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
  data() {
    return {
      processedImage: "",
      originalImage: ""
    };
  },
  created() {
    this.processedImage = "../assets/" + this.imgName + ".jpg";
    this.originalImage = "../assets/" + this.imgName + "Original.jpg";
  },
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
  z-index: 1000;
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
  transition: opacity 600ms ease-in, transform 600ms ease-in;
}

.image--original:hover {
  opacity: 0;
}
.image__container {
  position: relative;
  top: 50%;
  transform: translate(0%, -50%);
}
.closeBtn {
  width: 10vw;
  position: absolute;
  z-index: 2000;
  right: 10px;
  top: 10px;
}
@media (orientation: landscape) {
  .imageModal {
    padding: 0vw 5vw;
    box-sizing: border-box;
  }
}
</style>