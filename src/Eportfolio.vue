<template>
  <div id="app">
    <NavigationBar v-if="loaded"></NavigationBar>
    <ContentContainer v-if="loaded"></ContentContainer>
    <StartOverlay @setLoaded="setLoaded"></StartOverlay>
  </div>
</template>

<script>
import NavigationBar from "./components/NavigationBar.vue";
import Logo from "./components/Logo.vue";
import ContentContainer from "./components/ContentContainer.vue";
import StartOverlay from "./components/StartOverlay.vue";

import gsap from "gsap";

export default {
  name: "e-portfolio",
  components: {
    NavigationBar,
    Logo,
    ContentContainer,
    StartOverlay
  },
  data() {
    return {
      loaded: false
    };
  },
  methods: {
    setLoaded(status) {
      this.loaded = status;
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Nunito+Sans&display=swap");
* {
  font-family: "Nunito Sans", sans-serif;
}
#app {
  height: 100vh;
  padding: 0px;
  margin: 0px;
  overflow: hidden;
  background-color: #cf5230;
}
html,
body {
  margin: 0px;
  padding: 0px;
}
</style>
