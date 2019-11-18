<template>
  <div class="startOverlay" ref="startOverlay">
    <div class="startOverlay__bar--red"></div>
    <div class="startOverlay__bar--brown" ref="barBrown">
      <div ref="logo" class="logo">
        <svg
          version="1.1"
          id="Ebene_1"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          x="0px"
          y="0px"
          viewBox="0 0 997 997"
          style="enable-background:new 0 0 997 997;"
          xml:space="preserve"
        >
          <title>autumn-juggling-icon</title>
          <circle class="st0" cx="498.5" cy="498.5" r="498.5" />
          <path
            ref="leafYellow"
            class="st1 leafYellow"
            d="M479.3,233.6c7.4-14.8,28.5-59.4,21.6-72.4c-8.3-15.8-17.5-23.3-46.5-23.3s-71.5,15-71.5,15s2.5,6.6-2.5,8.3
	c0,0-18.3-5-42.4,5s-38.2,13.3-69.8,41.5l8.3,7.5c0,0-69,51.5-68.1,55.7s5,2.5,5,2.5c-12,7.9-21.1,19.6-25.8,33.2
	c-7.5,22.4-19.1,29.1-19.1,29.1s-17.4,19.9-17.4,28.3s5.8,7.5,5.8,7.5s-53.2,133.8,6.7,265.9l10.8-13.3c0,0-19.9,85.6,126.3,173.6
	c0,0-50.7-144.6-11.6-176.1c0,0,3.3-3.3,4.2,0.8s4.2,12.5,31.6-76.4c0,0,5.8-3.3,12.5,1.7l22.4-29.9c0,0-1.7-30.7,9.1-33.2
	l19.9,31.6c0,0,5-53.2,9.1-49c0,0,5.8-2.5,7.5,4.2c0,0,10-17.5,20.8-15l5.8,17.4c-0.2-0.5-1.8-8.3,43.2-9.9
	c46.5-1.7,72.3-33.2,72.3-33.2l17.4,11.6c0,0,10,0.8,22.4-9.1s0.8-39,39.9-40.7s11.6-73.9,11.6-73.9s-1.7-37.4-7.5-50.7
	s-29.1-37.4-29.1-37.4s-7.5-5-56.5-10.8l-49.8,15l-2.3,0.5l0.6-0.5"
          />
          <path
            ref="pathBrown"
            class="st0"
            d="M693.1,185.3c0,0-682.9,91.4-392.1,612.3c0,0-373-497.7,385.5-653.9L693.1,185.3z"
          />
          <circle
            ref="circleYellow"
            class="st1"
            cx="647.9"
            cy="168.2"
            r="55.3"
          />
          <path
            ref="leafRed"
            class="st2 leafRed"
            d="M526.5,776.7c-7.4,14.8-28.5,59.3-21.6,72.5c8.3,15.8,17.5,23.3,46.5,23.3c29.1,0,71.4-15,71.4-15
	s-2.5-6.6,2.5-8.3c0,0,18.3,5,42.4-5s38.2-13.3,69.8-41.5l-8.3-7.5c0,0,69-51.5,68.1-55.7s-5-2.5-5-2.5c12-7.9,21.1-19.6,25.8-33.2
	c7.5-22.4,19.1-29.1,19.1-29.1s17.4-19.9,17.4-28.3s-5.8-7.5-5.8-7.5S902,505.1,842.2,373l-10.8,13.3c0,0,19.9-85.6-126.3-173.6
	c0,0,50.7,144.6,11.6,176.1c0,0-3.3,3.3-4.2-0.8s-4.2-12.5-31.6,76.4c0,0-5.8,3.3-12.5-1.7l-22.4,29.9c0,0,1.7,30.7-9.1,33.2
	L617,494.3c0,0-5,53.2-9.1,49c0,0-5.8,2.5-7.5-4.2c0,0-10,17.4-20.8,15l-5.8-17.4c0.2,0.5,1.8,8.3-43.2,9.9
	c-46.5,1.7-72.3,33.2-72.3,33.2l-17.4-11.6c0,0-10-0.8-22.4,9.1s-0.8,39-39.9,40.7s-11.6,74-11.6,74s1.7,37.4,7.5,50.7
	s29.1,37.4,29.1,37.4s7.5,5,56.5,10.8l49.8-15l2.3-0.5l-0.6,0.5"
          />
          <path
            class="st0"
            d="M312.6,825c0,0,683-91.4,392.2-612.3c0,0,373,497.7-385.5,653.9L312.6,825z"
          />
          <circle ref="circleRed" class="st2" cx="357.1" cy="842" r="55.3" />
        </svg>
      </div>
    </div>
    <div class="startOverlay__bar--yellow"></div>
  </div>
</template>

<script>
import gsap from "gsap";

export default {
  name: "StartOverlay",
  mounted: function() {
    var timeline = gsap.timeline({ onComplete: this.showWebsite });
    timeline.fromTo(
      this.$refs.logo,
      { scale: 0 },
      {
        duration: 1.5,
        rotation: 720,
        transformOrigin: "center",
        scale: 1,
        ease: "power1.in"
      }
    );
    timeline.fromTo(
      [this.$refs.leafYellow, this.$refs.leafRed],
      1,
      { opacity: 0 },
      { opacity: 1, ease: "EaseInOut" }
    );
    timeline.to(this.$refs.startOverlay, 3, {
      rotation: 90,
      height: "100vw",
      //   width: "100vh",
      gridTemplateColumns: "0vh 10vh 90vh"
    });
    timeline.to(
      this.$refs.logo,
      3,
      {
        rotation: 630,
        transformOrigin: "center"
      },
      "<"
    );
  },
  methods: {
    showWebsite() {
      this.$emit("setLoaded", true);
    }
  }
};
</script>

<style scoped>
.startOverlay {
  width: 100vw;
  height: 100vh;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}
.startOverlay__bar--red {
  background-color: #cf5230;
}
.startOverlay__bar--brown {
  background-color: #997c67;
}
.startOverlay__bar--yellow {
  background-color: #dba72e;
}
.logo {
  position: relative;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.st0 {
  fill: #997c67;
}
.st1 {
  fill: #dba72e;
}
.st2 {
  fill: #cf5230;
}
</style>
