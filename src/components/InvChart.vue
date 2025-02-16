<script setup>
import { ref, onMounted } from "vue";
import { Chart, registerables } from "chart.js";
const props = defineProps(["datasets"]);

Chart.register(...registerables);

const chartCanvas = ref(null);

onMounted(() => {
  const ctx = chartCanvas.value.getContext("2d");

  const labels = ["", "", "", "", "", "", ""];

  new Chart(ctx, {
    type: "line",
    data: {
      labels,
      datasets: props.datasets,
    },
    options: {
      responsive: true,
      scales: {
        x: {
          grid: {
            display: false,
          },
          display: true,
          title: {
            display: false,
            text: "Month",
          },
        },
        y: {
          grid: {
            display: true,
          },
          display: true,
          title: {
            display: false,
            text: "Value",
          },
        },
      },
      plugins: {
        tooltip: {
          mode: "index",
          intersect: false,
        },
        legend: {
          display: false,
        },
      },
      interaction: {
        mode: "index",
        intersect: false,
      },
    },
  });
});
</script>
<template>
  <div>
    <canvas ref="chartCanvas"></canvas>
  </div>
</template>
<style scoped>
canvas {
  margin: 0 auto;
  display: block;
  height: 100%;
  width: 100%;
}

div {
  /* width: 100%; */

  /* height: 100%; */
}
</style>
