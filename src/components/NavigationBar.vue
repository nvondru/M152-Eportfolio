<template>
  <nav class="navigation-bar">
    <a ref="navItem1" href>Pictures</a>
    <a href>
      <img class="logo" src="../assets/logo.svg" alt="logo for eportfolio" />
    </a>
    <a ref="navItem2" href>Film</a>
  </nav>
</template>

<script>
import gsap from "gsap";

export default {
  name: "NavigationBar",
  props: {},
  mounted() {
    gsap.fromTo(
      [this.$refs.navItem1, this.$refs.navItem2],
      2,
      { opacity: 0 },
      { opacity: 1 }
    );
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.navigation-bar {
  width: 100%;
  display: grid;
  background-color: #997c67;
  position: absolute;
  z-index: 10;
  grid-template-columns: 4fr 1fr 4fr;
}
.logo {
  width: 10vh;
  height: 10vh;
}

a {
  color: #6e352c;
  text-decoration: none;
  justify-content: center;
  align-items: center;
  display: flex;
  font-size: 30px;
}
</style>
