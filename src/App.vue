<template>
  <div ref="gsapScena" id="app">
    <GsapScene />
  </div>
</template>

<script>
import GsapScene from "../public/scena.svg";
import gsap from "gsap";

export default {
  name: "App",
  components: {
    GsapScene,
  },
  methods: {},
  mounted: function () {
    const [elements] = this.$refs.gsapScena.children; //destrukturyzacja tablicy(wrzucanie do niej childrenow refa)

    console.log(elements);

    const postac = elements.getElementById("postac");
    const telefon = elements.getElementById("telefon");
    const drzewa = elements.getElementById("drzewa");
    const podloga = elements.getElementById("podloga");

    gsap.set([telefon, postac, drzewa, podloga], { autoAlpha: 0 });

    const tl = gsap.timeline({ defaults: { ease: "power3.inOut" } });

    tl.fromTo(drzewa, { x: "0" }, { duration: 1, x: "0", autoAlpha: 1 })
      .fromTo(
        telefon,
        { y: "-=300" },
        { duration: 1, y: "+=300", autoAlpha: 1 }
      )
      .fromTo(postac, { x: "+=300" }, { duration: 1, x: "-=300", autoAlpha: 1 })
      .fromTo(podloga, { x: "0" }, { duration: 1, x: "0", autoAlpha: 1 });
  },
};
</script>

<style>
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #4d5664;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
}
</style>
