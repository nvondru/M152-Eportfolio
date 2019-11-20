<template>
  <nav class="navigation-bar" ref="navigationBar">
    <a @click="handleClick('pictures')" class="link" href="#pictures">Pictures</a>
    <a @click="handleClick('welcome')" class="logo" ref="logo" href="#welcome">
      <Logo :scrolledPercent="scrolledPercent" @logoLoaded="loadNavigationBar"></Logo>
    </a>
    <a @click="handleClick('movie')" class="link" href="#movie">Movie</a>
  </nav>
</template>

<script>
import gsap from "gsap";
import Logo from "./Logo";

export default {
  name: "NavigationBar",
  components: {
    Logo
  },
  props: ["scrolledPercent"],
  data() {
    return {};
  },

  methods: {
    loadNavigationBar() {
      this.$emit("logoLoaded");
      var timeline = gsap.timeline();
      timeline.to(this.$refs.navigationBar, 2, {
        gridTemplateColumns: "1fr 9vh 1fr"
      });
      timeline.to(".link", 2, { opacity: 1 }, "<");
    },
    handleClick(target) {
      this.$emit("navigate", target);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.navigation-bar {
  display: grid;
  background-color: #997c67;
  grid-template-columns: 33.33vw 33.33vw 33.33vw;
  text-align: center;
}

a {
  text-decoration: none;
  justify-content: center;
  align-items: center;
  display: flex;
  font-size: 30px;
  cursor: pointer;
  transition: transform 100ms;
}

.link {
  opacity: 0;
}

@media only screen and (max-width: 600px) {
  a {
    font-size: 15px;
  }
}

@media only screen and (max-width: 900px) {
  a {
    font-size: 20px;
  }
}
</style>
