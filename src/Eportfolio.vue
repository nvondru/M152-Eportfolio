<template>
  <div id="app">
    <NavigationBar></NavigationBar>
    <ContentContainer></ContentContainer>
  </div>
</template>

<script>
import NavigationBar from "./components/NavigationBar.vue";
import Logo from "./components/Logo.vue";
import ContentContainer from "./components/ContentContainer.vue";

export default {
  name: "e-portfolio",
  components: {
    NavigationBar,
    Logo,
    ContentContainer
  }
};
</script>

<style>
#app {
  width: 100%;
  height: 100%;
  padding: 0px;
  margin: 0px;
  display: grid;
  grid-template-rows: 1fr 9fr;
  overflow: hidden;
}
html,
body {
  margin: 0px;
  padding: 0px;
}
</style>
