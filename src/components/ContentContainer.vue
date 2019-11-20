<template>
  <div @scroll="handleScroll($event)" class="content-container" ref="contentContainer">
    <div class="content" ref="content">
      <section id="welcome" class="content__welcome" ref="welcome">
        <hr />
        <h1>Welcome to my E-Portfolio "Juggling in autumn"</h1>
        <hr />
        <p>The work in this Portfolio is dedicated to the arts of Juggling. Because this project was elaborated in autumn, the pictures and the website are kept in an autumn flavoured style.</p>
        <p>The logo was built first and serves as core element for the rest of the Website.</p>
        <p class="logo">
          <Logo></Logo>
        </p>
      </section>
      <section id="pictures" class="content__pictures" ref="pictures">
        <hr />
        <h1>Pictures</h1>
        <hr />
        <p class="pictureContainer">
          <img src="../assets/forestGate.jpg" alt />
          Lorem ipsum dolor sit amet consectetur adipisicing elit. At consequatur, neque veniam aut ad omnis id quia voluptas nisi voluptate. Minus rerum ullam a neque ipsum dolores ducimus odio atque sed, minima, doloribus voluptates consequuntur obcaecati, exercitationem nulla eum perferendis vero sequi molestias! Et doloribus, fuga saepe temporibus incidunt quis asperiores dolore nostrum illo alias provident at nesciunt, cum fugit! Temporibus velit doloribus incidunt labore similique suscipit placeat animi libero corporis pariatur ad, facilis cupiditate aliquam eveniet, recusandae ducimus at saepe modi inventore. Veniam assumenda reprehenderit aliquam similique cumque voluptatibus ut accusamus doloribus voluptatum ipsum odio, quidem eligendi magnam deserunt omnis magni inventore sit? Amet modi laborum neque voluptatibus eum, deleniti eius odit repudiandae nemo ratione soluta blanditiis sint? Cupiditate sunt vero totam neque assumenda quas repudiandae ducimus architecto ea hic exercitationem blanditiis adipisci delectus ipsam, pariatur modi laboriosam molestiae quis qui. Eos velit corrupti eligendi totam animi, ab deserunt.
        </p>
      </section>
      <section id="movie" class="content__film" ref="movie">
        <hr />
        <h1>Movie</h1>
        <hr />
        <p class="movieContainer">
          <iframe
            src="https://www.youtube.com/embed/TGcpovKTULM"
            frameborder="0"
            allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
          ></iframe>
        </p>
      </section>
    </div>
  </div>
</template>

<script>
import gsap from "gsap";
import Logo from "./Logo";
export default {
  name: "ContentContainer",
  components: {
    Logo
  },
  props: ["loaded", "navigationTarget"],
  watch: {
    loaded: {
      handler() {
        if (this.loaded) {
          gsap.to(this.$refs.content, 2, { opacity: 1, display: "block" });
        }
      }
    },
    navigationTarget: {
      handler() {}
    }
  },
  methods: {
    handleScroll(event) {
      let scrolledUnits = this.$refs.contentContainer.scrollTop;
      let height =
        this.$refs.contentContainer.scrollHeight -
        document.body.clientHeight +
        document.body.clientHeight / 10;
      let scrolledPercent = Math.round((scrolledUnits / height) * 100);
      this.$emit("scrolled", scrolledPercent);
    }
  }
};
</script>

<style scoped>
.content-container {
  width: 100%;
  text-align: center;
  overflow-y: auto;
  scroll-behavior: smooth;

  /* #CF5230 */
  background-color: #dba72e;
  padding: 2vw 15vw;
  box-sizing: border-box;
}
@media only screen and (max-width: 900px) {
  .content-container {
    padding: 2vw 6vw;
  }
  p {
    font-size: 2px;
  }
}
.content {
  opacity: 0;
  display: none;
}
hr {
  background-color: #6e352c;
  color: #6e352c;
  border: 2px #6e352c solid;
}
.pictureContainer {
  padding: 4% 10%;
}
img {
  width: 100%;
}
p {
  font-size: 1.5rem;
}
h1 {
  font-size: 200%;
}
iframe {
  width: 64vw;
  height: 36vw;
}
</style>