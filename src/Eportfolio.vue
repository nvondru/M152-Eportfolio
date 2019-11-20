<template>
  <div id="app" ref="app" class="noEvents">
    <div class="bar--red"></div>
    <NavigationBar @logoLoaded="loadWebsite" :scrolledPercent="scrolledPercent"></NavigationBar>
    <ContentContainer @scrolled="setScrolled" :loaded="loaded" :navigationTarget="target"></ContentContainer>
  </div>
</template>

<script>
import NavigationBar from "./components/NavigationBar.vue";
import ContentContainer from "./components/ContentContainer.vue";

import gsap from "gsap";

export default {
  name: "e-portfolio",
  components: {
    NavigationBar,
    ContentContainer
  },
  data() {
    return {
      loaded: false,
      scrolledPercent: 0,
      target: "welcome"
    };
  },

  methods: {
    loadWebsite() {
      this.loaded = true;
      var timeline = gsap.timeline({
        onComplete: () => this.$refs.app.classList.remove("noEvents")
      });
      timeline.to(this.$refs.app, 1.5, {
        gridTemplateRows: "0vh 10vh 90vh",
        ease: "EaseInOut"
      });
    },
    setScrolled(scrolledPercent) {
      this.scrolledPercent = scrolledPercent;
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Nunito+Sans&display=swap");
* {
  font-family: "Nunito Sans", sans-serif;
  color: #6e352c;
}
#app {
  height: 100vh;
  padding: 0px;
  margin: 0px;
  overflow: hidden;
  display: grid;
  grid-template-rows: 1fr 2fr 1fr;
}
.noEvents {
  pointer-events: none;
}
html,
body {
  margin: 0px;
  padding: 0px;
}
::-webkit-scrollbar {
  display: none;
}
.bar--red {
  background-color: #cf5230;
}
</style>
