<template>
  <div id="app">
    <canvas id="myChart"></canvas>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import { Chart } from "chart.js";

export default Vue.extend({
  name: "App",
  mounted() {
    const ctx = (
      document.getElementById("myChart") as HTMLCanvasElement
    ).getContext("2d");
    const cart = new Chart(ctx, {
      type: "line",
      data: {
        labels: ["January", "February", "April", "May", "June", "July"],
        datasets: [
          {
            label: "My first dataset",
            backgroundColor: "rgb(255,99,132)",
            borderColor: "rgb(255, 99, 132)",
            data: [0, 10, 5, 2, 20, 30, 45],
          },
        ],
      },
      options: {},
    });
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
