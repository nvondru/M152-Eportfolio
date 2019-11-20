<template>
  <div class="startOverlay" ref="startOverlay"></div>
</template>

<script>
import gsap from "gsap";

export default {
  name: "StartOverlay",
  mounted: function() {},
  methods: {
    showWebsite() {
      this.$emit("setLoaded", true);
    }
  }
};
</script>

<style scoped>
.startOverlay {
  width: 100vw;
  height: 100vh;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}
.startOverlay__bar--red {
  background-color: #cf5230;
}
.startOverlay__bar--brown {
  background-color: #997c67;
  text-align: center;
}
.startOverlay__bar--yellow {
  background-color: #dba72e;
}
.logo {
  position: relative;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
