<script setup>
import { ref, onMounted } from "vue";
import { Chart, registerables } from "chart.js";

// Register Chart.js components
Chart.register(...registerables);

const chartCanvas = ref(null);

onMounted(() => {
  const ctx = chartCanvas.value.getContext("2d");

  const labels = ["", "", "", "", "", ""];
  const minData = [5, 7, 5, 6, 8, 10];
  const maxData = [5, 7, 12, 13, 15, 18];
  const meanData = [5, 7, 9, 10, 12, 14];

  new Chart(ctx, {
    type: "line",
    data: {
      labels,
      datasets: [
        {
          label: "Min",
          data: minData,
          borderColor: "rgba(0,0,0,0)",
          backgroundColor: "rgba(0,0,0,0)",
          pointRadius: 0,
          fill: false,
          order: 1,
          tension: 0,
        },
        {
          label: "Max",
          data: maxData,
          borderColor: "rgba(0,0,0,0)",
          backgroundColor: "rgba(255, 99, 132, 0.2)",
          pointRadius: 0,
          fill: "-1",
          order: 2,
          tension: 0,
        },
        {
          label: "Mean",
          data: meanData,
          borderColor: "rgb(54, 162, 235)",
          backgroundColor: "rgba(54, 162, 235, 0.1)",
          pointRadius: 4,
          fill: false,
          borderWidth: 2,
          order: 3,
          tension: 0,
        },
      ],
    },
    options: {
      responsive: true,
      scales: {
        x: {
          display: true,
          title: {
            display: false,
            text: "Month",
          },
        },
        y: {
          grid: {
            display: false,
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
          display: true,
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
  <section>
    <canvas ref="chartCanvas"></canvas>
  </section>
</template>
<style scoped>
canvas {
  margin: 0 auto;
  display: block;
  height: 100%;
  width: 100%;
}

section {
  width: 100%;
  height: 100vh;
}
</style>
