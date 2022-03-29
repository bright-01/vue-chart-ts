<template>
  <div id="app">
    <canvas id="myChart"></canvas>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Chart from "chart.js/auto";
import { ChartConfiguration } from "chart.js";

export default Vue.extend({
  name: "App",
  mounted() {
    const labels = ["January", "February", "March", "April", "May", "June"];
    const data = {
      labels: labels,
      datasets: [
        {
          label: "My First dataset",
          backgroundColor: "rgb(255, 99, 132)",
          borderColor: "rgb(255, 99, 132)",
          data: [0, 10, 5, 2, 20, 30, 45],
        },
      ],
    };
    const config: ChartConfiguration = {
      type: "line",
      data,
      options: {},
    };
    const ctx = (
      document.getElementById("myChart") as HTMLCanvasElement
    ).getContext("2d") as CanvasRenderingContext2D;
    let myChart = new Chart(ctx, config);
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
