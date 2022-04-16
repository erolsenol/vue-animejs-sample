<template>
  <div class="container">
    <div v-text="{ charged: battery.charged, cycles: battery.cycles }"></div>
    <div class="box one"></div>
    <div class="box two"></div>
  </div>
  <div class="action">
    <button @click="startAction">Start</button>
  </div>
</template>

<script>
import anime from "animejs/lib/anime.es.js";
export default {
  name: "HelloWorld",
  data() {
    return {
      battery: {
        charged: "0%",
        cycles: 120,
      },
    };
  },
  methods: {
    startAction() {
      const els = document.querySelectorAll(".box");
      anime({
        targets: els,
        left: "240px",
        backgroundColor: "#cf7e12",
        borderRadius: ["0%", "50%"],
        translateX: 250,
        easing: "easeInOutQuad",
      });

      anime({
        targets: this.battery,
        charged: "100%",
        cycles: 130,
        round: 1,
        easing: "linear",
      });
    },
  },
  mounted() {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.container {
  width: 100%;
  height: 100%;
  justify-content: center;
  align-items: center;
  padding: 20px;
  .box {
    height: 50px;
    width: 50px;
    background-color: rgb(255, 0, 0);
  }
  .two {
    margin-top: 10px;
  }
}
</style>
