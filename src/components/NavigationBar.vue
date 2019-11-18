<template>
  <nav class="navigation-bar">
    <a href>Pictures</a>
    <a href>
      <img class="logo" src="../assets/logo.svg" alt="logo for eportfolio" />
    </a>
    <a href>Pictures</a>
  </nav>
</template>

<script>
export default {
  name: "NavigationBar",
  props: {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.navigation-bar {
  width: 100%;
  display: grid;
  background-color: #997c67;
  position: relative;
  grid-template-columns: 4fr 1fr 4fr;
  max-height: 100px;
}
.logo {
  width: 100%;
  height: 100%;
  max-height: 80px;
}
a {
  color: #6e352c;
  font-size: ;
}
</style>
