<template>
  <div @scroll="handleScroll($event)" class="content-container" ref="contentContainer">
    <div id="welcome" class="content--invisible" ref="content">
      <section class="content--yellow">
        <section class="content__welcome" ref="welcome">
          <hr />
          <h1>Welcome to my E-Portfolio "Juggling in autumn"</h1>
          <hr />
          <article class="articleContainer">
            <p>The work in this Portfolio is dedicated to the arts of juggling. Because this project was elaborated in autumn, the pictures and the website are kept in an autumn flavoured style.</p>
            <p>The logo was built first and serves as the core element for the rest of the website.</p>
            <img ref="logoImg" @click="openModal($event)" class="logo" src="../assets/logo.svg" alt />
          </article>
        </section>
        <section id="pictures" class="content__pictures" ref="pictures">
          <hr />
          <h1>Pictures</h1>
          <hr />
          <article class="articleContainer">
            <div class="image__container" ref="firstPicture">
              <img
                class="image--processed"
                @click="openModal($event)"
                src="../assets/forestGate.jpg"
                alt
              />
              <img class="image--original" src="../assets/forestGateOriginal.jpg" alt />
            </div>
            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facere vel aliquid rem pariatur. Vitae voluptates accusantium ea deleniti nihil exercitationem esse quis, recusandae at? Ducimus obcaecati in ipsum, beatae ea corporis, molestias quisquam dignissimos fugiat incidunt illo odit recusandae veritatis dicta consequuntur repudiandae! Voluptates, itaque distinctio amet repellat nostrum laborum saepe veritatis a laudantium quisquam odit reiciendis earum, aperiam enim, natus necessitatibus? Corrupti dolor magni aspernatur vero, placeat veniam voluptas perferendis magnam cumque nisi ad nam exercitationem! Sint explicabo, minus earum excepturi magni incidunt modi reiciendis id dolorem tempore doloribus temporibus harum a itaque. Odio sapiente quos maxime consectetur quae?</p>
          </article>
          <article class="articleContainer">
            <div class="image__container">
              <img
                class="image--processed"
                @click="openModal($event)"
                src="../assets/autumnLeaves.jpg"
                alt
              />
              <img class="image--original" src="../assets/autumnLeavesOriginal.jpg" alt />
            </div>
            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facere vel aliquid rem pariatur. Vitae voluptates accusantium ea deleniti nihil exercitationem esse quis, recusandae at? Ducimus obcaecati in ipsum, beatae ea corporis, molestias quisquam dignissimos fugiat incidunt illo odit recusandae veritatis dicta consequuntur repudiandae! Voluptates, itaque distinctio amet repellat nostrum laborum saepe veritatis a laudantium quisquam odit reiciendis earum, aperiam enim, natus necessitatibus? Corrupti dolor magni aspernatur vero, placeat veniam voluptas perferendis magnam cumque nisi ad nam exercitationem! Sint explicabo, minus earum excepturi magni incidunt modi reiciendis id dolorem tempore doloribus temporibus harum a itaque. Odio sapiente quos maxime consectetur quae?</p>
          </article>
        </section>
      </section>

      <section id="movie" class="content--red" ref="movie">
        <section class="content__film">
          <hr />
          <h1>Movie</h1>
          <hr />
          <article class="articleContainer">
            <iframe
              src="https://www.youtube.com/embed/TGcpovKTULM"
              frameborder="0"
              allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
              allowfullscreen
            ></iframe>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Velit unde ducimus fugit dignissimos libero commodi dolorem dicta veritatis harum ut, hic architecto nisi a quaerat necessitatibus tempora modi sed maiores nesciunt consequatur accusamus totam animi aliquam! Consequuntur nihil nam atque illo ad distinctio, dolorum facilis. Repellat debitis necessitatibus quisquam, officia odio reiciendis? Corrupti, impedit. Vel sunt labore obcaecati sit, illum eum praesentium perferendis voluptatum in, id harum sequi cum, neque ipsam corporis laborum est ad atque quaerat reiciendis distinctio itaque culpa nostrum? Necessitatibus nesciunt aperiam vero cupiditate qui, magni ab quas quos doloremque nihil accusamus a, dolorum ipsam eligendi. Quia.</p>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Velit unde ducimus fugit dignissimos libero commodi dolorem dicta veritatis harum ut, hic architecto nisi a quaerat necessitatibus tempora modi sed maiores nesciunt consequatur accusamus totam animi aliquam! Consequuntur nihil nam atque illo ad distinctio, dolorum facilis. Repellat debitis necessitatibus quisquam, officia odio reiciendis? Corrupti, impedit. Vel sunt labore obcaecati sit, illum eum praesentium perferendis voluptatum in, id harum sequi cum, neque ipsam corporis laborum est ad atque quaerat reiciendis distinctio itaque culpa nostrum? Necessitatibus nesciunt aperiam vero cupiditate qui, magni ab quas quos doloremque nihil accusamus a, dolorum ipsam eligendi. Quia.</p>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Velit unde ducimus fugit dignissimos libero commodi dolorem dicta veritatis harum ut, hic architecto nisi a quaerat necessitatibus tempora modi sed maiores nesciunt consequatur accusamus totam animi aliquam! Consequuntur nihil nam atque illo ad distinctio, dolorum facilis. Repellat debitis necessitatibus quisquam, officia odio reiciendis? Corrupti, impedit. Vel sunt labore obcaecati sit, illum eum praesentium perferendis voluptatum in, id harum sequi cum, neque ipsam corporis laborum est ad atque quaerat reiciendis distinctio itaque culpa nostrum? Necessitatibus nesciunt aperiam vero cupiditate qui, magni ab quas quos doloremque nihil accusamus a, dolorum ipsam eligendi. Quia.</p>
          </article>
        </section>
      </section>
    </div>
    <Footer></Footer>
  </div>
</template>

<script>
import gsap from "gsap";
import Logo from "./Logo";
import Footer from "./Footer";

export default {
  name: "ContentContainer",
  components: {
    Logo,
    Footer
  },
  props: ["loaded"],
  data() {
    return {
      scrolledUnits: 0,
      activeContent: "welcome"
    };
  },
  watch: {
    loaded: {
      handler() {
        if (this.loaded) {
          gsap.to(this.$refs.content, 1.5, { opacity: 1, ease: "EaseInOut" });
          gsap.from(this.$refs.logoImg, 1.5, {
            top: "-200%",
            scale: "0",
            rotation: "720deg",
            ease: "EaseInOut"
          });
        }
      }
    }
  },
  mounted() {},
  methods: {
    handleScroll(event) {
      this.scrolledUnits = this.$refs.contentContainer.scrollTop;
      let height =
        this.$refs.contentContainer.scrollHeight -
        document.body.clientHeight +
        document.body.clientHeight / 10;
      let scrolledPercent = Math.round((this.scrolledUnits / height) * 100);

      if (this.scrolledTo("movie")) {
        this.activeContent = "movie";
      } else {
        this.activeContent = "pictures";
      }

      if (this.scrolledTo("pictures")) {
        this.$emit("reachedFirstPicture");
      }

      this.$emit("scrolled", scrolledPercent, this.activeContent);
    },
    openModal(event) {
      console.log(event.target.src);
    },
    scrolledTo(elem) {
      // console.log(this.scrolledUnits);
      // console.log(this.$refs[elem].offsetTop - document.body.clientHeight / 10);

      let elemPosition =
        this.$refs[elem].offsetTop - document.body.clientHeight / 10;
      if (
        this.scrolledUnits >= elemPosition ||
        !(Math.abs(this.scrolledUnits - elemPosition) > 1)
      ) {
        return true;
      }
      return false;
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
  box-sizing: border-box;
}

.content--invisible {
  opacity: 0;
}
.content--yellow {
  /* background-color: #dba72e; */
  padding: 2vw 12vw;
}
.content--red {
  background-color: #cf5230;
  padding: 2vw 12vw;
}
.content--red * {
  color: #e6c098;
}
.content--red hr {
  background-color: #e6c098;
  color: #e6c098;
  border: 2px #e6c098 solid;
}
hr {
  background-color: #6e352c;
  color: #6e352c;
  border: 2px #6e352c solid;
}
.articleContainer {
  margin: 4% 10%;
}
img {
  width: 100%;
  border-radius: 1vw;
  cursor: pointer;
  margin: 0px;
  padding: 0px;
  display: block;
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
.logo {
  max-width: 400px;
  display: initial;
  position: relative;
}

@media only screen and (max-width: 1200px) {
  .content {
    padding: 2vw 8vw;
  }
  .articleContainer {
    margin: 4% 6%;
  }
  p {
    font-size: 1.3rem;
  }
}

@media only screen and (max-width: 900px) {
  .content {
    padding: 2vw 6vw;
  }
  .articleContainer {
    margin: 4% 4%;
  }
  p {
    font-size: 1.2rem;
  }
}
</style>