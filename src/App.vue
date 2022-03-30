<template>
  <div id="app">
    <canvas id="myChart" ref="myChart"></canvas>
  </div>
</template>

<script lang="ts">
import Vue, { VueConstructor } from "vue";
// import Chart from "chart.js/auto";
import { ChartConfiguration } from "chart.js";
import { MyVueRefs } from "@/types";

// export default (
//   Vue as VueConstructor<Vue & { $ref: { myChart: HTMLCanvasElement } }>
// ).extend({

export default (Vue as MyVueRefs<{ myChart: HTMLCanvasElement }>).extend({
  name: "App",
  methods: {
    sayHi() {
      const canvasElement = this.$refs.myChart;
      console.log(canvasElement);
    },
  },

  mounted() {
    // const cavasElement = document.getElementById(
    //   "myChart"
    // ) as HTMLCanvasElement;
    // const ctx2 = cavasElement.getContext("2d");
    //
    // if (!ctx2) {
    //   return;
    // }
    // const chart2 = new Chart(ctx2, {}); // null 일 수도 있어서 에러가 발생

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
    // const ctx = (
    //   document.getElementById("myChart") as HTMLCanvasElement
    // ).getContext("2d") as CanvasRenderingContext2D;

    const canvasElement = this.$refs.myChart;
    const ctx = canvasElement.getContext("2d");
    let myChart = new this.$_Chart(10, config);
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
