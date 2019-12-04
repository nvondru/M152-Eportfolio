<template>
  <div @scroll="handleScroll($event)" class="content-container" ref="contentContainer">
    <div id="welcome" class="content--invisible" ref="content">
      <section class="content content--yellow">
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
            <div
              class="image__container"
              ref="firstPicture"
              @click="openModal('forestGate', $event)"
              @contextmenu="openModal('forestGate', $event)"
            >
              <img class="image--processed" src="../assets/forestGate.jpg" alt />
              <img class="image--original" src="../assets/forestGateOriginal.jpg" alt />
            </div>
            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facere vel aliquid rem pariatur. Vitae voluptates accusantium ea deleniti nihil exercitationem esse quis, recusandae at? Ducimus obcaecati in ipsum, beatae ea corporis, molestias quisquam dignissimos fugiat incidunt illo odit recusandae veritatis dicta consequuntur repudiandae! Voluptates, itaque distinctio amet repellat nostrum laborum saepe veritatis a laudantium quisquam odit reiciendis earum, aperiam enim, natus necessitatibus? Corrupti dolor magni aspernatur vero, placeat veniam voluptas perferendis magnam cumque nisi ad nam exercitationem! Sint explicabo, minus earum excepturi magni incidunt modi reiciendis id dolorem tempore doloribus temporibus harum a itaque. Odio sapiente quos maxime consectetur quae?</p>
          </article>
          <article class="articleContainer">
            <div
              class="image__container"
              @click="openModal('autumnLeaves', $event)"
              @contextmenu="openModal('autumnLeaves', $event)"
            >
              <img class="image--processed" src="../assets/autumnLeaves.jpg" alt />
              <img class="image--original" src="../assets/autumnLeavesOriginal.jpg" alt />
            </div>
            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facere vel aliquid rem pariatur. Vitae voluptates accusantium ea deleniti nihil exercitationem esse quis, recusandae at? Ducimus obcaecati in ipsum, beatae ea corporis, molestias quisquam dignissimos fugiat incidunt illo odit recusandae veritatis dicta consequuntur repudiandae! Voluptates, itaque distinctio amet repellat nostrum laborum saepe veritatis a laudantium quisquam odit reiciendis earum, aperiam enim, natus necessitatibus? Corrupti dolor magni aspernatur vero, placeat veniam voluptas perferendis magnam cumque nisi ad nam exercitationem! Sint explicabo, minus earum excepturi magni incidunt modi reiciendis id dolorem tempore doloribus temporibus harum a itaque. Odio sapiente quos maxime consectetur quae?</p>
          </article>
        </section>
      </section>

      <section id="movie" class="content content--red" ref="movie">
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
    <transition name="fade">
      <ImageModal
        v-if="imageModal.open"
        @closeImageModal="imageModal.open = false"
        :imgName="imageModal.imgName"
      ></ImageModal>
    </transition>
  </div>
</template>

<script>
import gsap from "gsap";
import Footer from "./Footer";
import ImageModal from "./ImageModal";

export default {
  name: "ContentContainer",
  components: {
    Footer,
    ImageModal
  },
  props: ["loaded"],
  data() {
    return {
      scrolledUnits: 0,
      activeContent: "welcome",
      isMobile: false,
      imageModal: {
        open: false,
        imgName: ""
      }
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
  mounted() {
    // device detection
    if (
      /(android|bb\d+|meego).+mobile|avantgo|bada\/|blackberry|blazer|compal|elaine|fennec|hiptop|iemobile|ip(hone|od)|ipad|iris|kindle|Android|Silk|lge |maemo|midp|mmp|netfront|opera m(ob|in)i|palm( os)?|phone|p(ixi|re)\/|plucker|pocket|psp|series(4|6)0|symbian|treo|up\.(browser|link)|vodafone|wap|windows (ce|phone)|xda|xiino/i.test(
        navigator.userAgent
      ) ||
      /1207|6310|6590|3gso|4thp|50[1-6]i|770s|802s|a wa|abac|ac(er|oo|s\-)|ai(ko|rn)|al(av|ca|co)|amoi|an(ex|ny|yw)|aptu|ar(ch|go)|as(te|us)|attw|au(di|\-m|r |s )|avan|be(ck|ll|nq)|bi(lb|rd)|bl(ac|az)|br(e|v)w|bumb|bw\-(n|u)|c55\/|capi|ccwa|cdm\-|cell|chtm|cldc|cmd\-|co(mp|nd)|craw|da(it|ll|ng)|dbte|dc\-s|devi|dica|dmob|do(c|p)o|ds(12|\-d)|el(49|ai)|em(l2|ul)|er(ic|k0)|esl8|ez([4-7]0|os|wa|ze)|fetc|fly(\-|_)|g1 u|g560|gene|gf\-5|g\-mo|go(\.w|od)|gr(ad|un)|haie|hcit|hd\-(m|p|t)|hei\-|hi(pt|ta)|hp( i|ip)|hs\-c|ht(c(\-| |_|a|g|p|s|t)|tp)|hu(aw|tc)|i\-(20|go|ma)|i230|iac( |\-|\/)|ibro|idea|ig01|ikom|im1k|inno|ipaq|iris|ja(t|v)a|jbro|jemu|jigs|kddi|keji|kgt( |\/)|klon|kpt |kwc\-|kyo(c|k)|le(no|xi)|lg( g|\/(k|l|u)|50|54|\-[a-w])|libw|lynx|m1\-w|m3ga|m50\/|ma(te|ui|xo)|mc(01|21|ca)|m\-cr|me(rc|ri)|mi(o8|oa|ts)|mmef|mo(01|02|bi|de|do|t(\-| |o|v)|zz)|mt(50|p1|v )|mwbp|mywa|n10[0-2]|n20[2-3]|n30(0|2)|n50(0|2|5)|n7(0(0|1)|10)|ne((c|m)\-|on|tf|wf|wg|wt)|nok(6|i)|nzph|o2im|op(ti|wv)|oran|owg1|p800|pan(a|d|t)|pdxg|pg(13|\-([1-8]|c))|phil|pire|pl(ay|uc)|pn\-2|po(ck|rt|se)|prox|psio|pt\-g|qa\-a|qc(07|12|21|32|60|\-[2-7]|i\-)|qtek|r380|r600|raks|rim9|ro(ve|zo)|s55\/|sa(ge|ma|mm|ms|ny|va)|sc(01|h\-|oo|p\-)|sdk\/|se(c(\-|0|1)|47|mc|nd|ri)|sgh\-|shar|sie(\-|m)|sk\-0|sl(45|id)|sm(al|ar|b3|it|t5)|so(ft|ny)|sp(01|h\-|v\-|v )|sy(01|mb)|t2(18|50)|t6(00|10|18)|ta(gt|lk)|tcl\-|tdg\-|tel(i|m)|tim\-|t\-mo|to(pl|sh)|ts(70|m\-|m3|m5)|tx\-9|up(\.b|g1|si)|utst|v400|v750|veri|vi(rg|te)|vk(40|5[0-3]|\-v)|vm40|voda|vulc|vx(52|53|60|61|70|80|81|83|85|98)|w3c(\-| )|webc|whit|wi(g |nc|nw)|wmlb|wonu|x700|yas\-|your|zeto|zte\-/i.test(
        navigator.userAgent.substr(0, 4)
      )
    ) {
      this.isMobile = true;
    }
  },
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
    openModal(imgName, event) {
      if (this.isMobile && event.type === "contextmenu") {
        event.preventDefault();
        this.createModal(imgName);
      } else if (!this.isMobile && event.type === "click") {
        this.createModal(imgName);
      }
    },
    createModal(imgName) {
      this.imageModal.imgName = imgName;
      this.imageModal.open = true;
    },
    scrolledTo(elem) {
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
.content {
  padding: 2vw 12vw;
}

.content--invisible {
  opacity: 0;
}

.content--red {
  background-color: #cf5230;
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
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
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
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease-in-out;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

@media only screen and (max-width: 1200px) {
  h1 {
    font-size: 150%;
  }
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
  h1 {
    font-size: 120%;
  }
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