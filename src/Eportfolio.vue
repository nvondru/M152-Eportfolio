<template>
  <div id="app" ref="app" class="noEvents">
    <div class="bar--red"></div>
    <NavigationBar
      @logoLoaded="loadWebsite"
      :scrolledPercent="scrolledPercent"
      :activeContent="activeContent"
    ></NavigationBar>
    <ContentContainer
      @scrolled="setScrolled"
      @reachedFirstPicture="showTutorialPanel"
      :loaded="loaded"
      ref="contentContainer"
    ></ContentContainer>
    <transition name="fade">
      <TutorialPanel
        v-show="tutorialActive"
        @closeTutorialPanel="tutorialActive = false"
        @openImageModal="openImageModal"
      ></TutorialPanel>
    </transition>
  </div>
</template>

<script>
import NavigationBar from "./components/NavigationBar.vue";
import ContentContainer from "./components/ContentContainer.vue";
import TutorialPanel from "./components/TutorialPanel";

import gsap from "gsap";

export default {
  name: "e-portfolio",
  components: {
    NavigationBar,
    ContentContainer,
    TutorialPanel
  },
  data() {
    return {
      loaded: false,
      scrolledPercent: 0,
      activeContent: "welcome",
      tutorialShown: false,
      tutorialActive: false
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
    setScrolled(scrolledPercent, activeContent) {
      this.scrolledPercent = scrolledPercent;
      this.activeContent = activeContent;
    },
    showTutorialPanel() {
      if (!this.tutorialShown) {
        this.tutorialShown = true;
        this.tutorialActive = true;
      }
    },
    openImageModal(imgName) {
      this.$refs.contentContainer.createModal(imgName);
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
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.8s ease-in-out;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
