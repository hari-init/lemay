<template>
  <div class="inventory-container">
    <div class="inventory-heading">
      <h1>Inventory Overview</h1>
    </div>

    <div class="data-container">
      <ul class="card-container">
        <li class="card-list" v-for="item in JSONData" :key="item.title">
          <Card :cardTitle="item.title" :cardValue="item.value" />
        </li>
      </ul>

      <ul class="chart-container">
        <li class="chart-list">
          <Card cardTitle="Balance by Aging Group" cardValue="">
            <InvChart
              :datasets="[
                {
                  label: 'Mean',
                  data: [0.5, 0.5, 0.9, 0.9, 1, 1, 1],
                  fill: true,
                  borderWidth: 1,
                  tension: 0.5,
                  backgroundColor: '#0d5945',
                  borderColor: '#11e5ab',
                  pointRadius: 0,
                },
                {
                  label: 'Mean',
                  data: [2.1, 1.8, 1.7, 1.5, 1, 1],
                  fill: true,
                  borderWidth: 1,
                  tension: 0,
                  backgroundColor: '#11e5ab',
                  borderColor: '#11e5ab',
                  pointRadius: 0,
                },
                {
                  label: 'Mean',
                  data: [4, 3.8, 3.7, 3.5, 3, 3, 3],
                  fill: true,
                  borderWidth: 1,
                  tension: 0,
                  backgroundColor: '#0c8c7b',
                  borderColor: '#11e5ab',
                  pointRadius: 0,
                },
              ]"
            />
          </Card>
        </li>
        <li class="chart-list">
          <Card cardTitle="% Items Out Of Stock" cardValue="">
            <InvChart
              :datasets="[
                {
                  label: 'Mean',
                  data: [0.1, 0.3, 0.29, 0.35, 0.46, 0.59, 0.48],
                  fill: false,
                  borderWidth: 1,
                  tension: 0,
                  backgroundColor: '#11e5ab',
                  borderColor: '#11e5ab',
                  pointRadius: 0,
                },
              ]"
            />
          </Card>
        </li>
        <li class="chart-list">
          <Card cardTitle="Cost Amount Purchase" cardValue="">
            <InvChart
              :datasets="[
                {
                  label: 'Mean',
                  data: [0.1, 0.2, 0.3, 0.1, 0.4, 0.1, 0.2],
                  pointRadius: 4,
                  fill: false,
                  borderWidth: 1,
                  tension: 0,
                  backgroundColor: '#11e5ab',
                  borderColor: '#11e5ab',
                  pointRadius: 0,
                },
              ]"
            />
          </Card>
        </li>
        <li class="chart-list">
          <Card cardTitle="Quantity Purchase" cardValue="">
            <InvChart
              :datasets="[
                {
                  label: 'Mean',
                  data: [0.1, 0.1, 0.1, 0.1, 0.5, 0.1, 0.2],
                  pointRadius: 4,
                  fill: false,
                  borderWidth: 1,
                  tension: 0,
                  backgroundColor: '#11e5ab',
                  borderColor: '#11e5ab',
                  pointRadius: 0,
                },
              ]"
            />
          </Card>
        </li>
      </ul>
    </div>
  </div>
</template>
<script setup>
import Card from "@/components/Card.vue";
import InvChart from "@/components/InvChart.vue";

const JSONData = [
  {
    title: "Balance",
    value: "4.03M",
  },
  {
    title: "Aging Balance",
    value: "2.05M",
  },
  {
    title: "Stock Quantity",
    value: "336K",
  },
  {
    title: "Cost Increase",
    value: "3.08M",
  },
  {
    title: "Cost Amount",
    value: "-1.95M",
  },
  {
    title: "Purchase Cost",
    value: "3.08M",
  },
  {
    title: "Sales Cost",
    value: "3.08M",
  },
  {
    title: "Cost Decrease",
    value: "7.97M",
  },
];
</script>
<style scoped>
.inventory-container {
  display: flex;
  flex-direction: column;
  background-color: #171635;
  width: 100%;
  height: 100%;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
}
.inventory-heading {
  color: white;
  font-size: 24px;
  display: flex;
  align-items: center;
  justify-content: left;
  width: 100%;
  margin-bottom: 20px;
}
.data-container {
  padding: 20px;
  background-color: #33325a;
  width: 75%;
  height: 90%;
}

.card-container {
  display: flex;
  flex-wrap: wrap;
  height: 30%;
}
.chart-container {
  display: flex;
  flex-wrap: wrap;
  height: 50%;
  margin-top: 50px;
}

.card-list {
  width: 25%;
  padding: 4px;
}
.chart-list {
  width: 50%;
  padding: 4px;
}

@media only screen and (max-width: 768px) {
  .data-container {
    width: 100%;
  }
  .card-list {
    width: 50%;
  }
  .chart-list {
    width: 100%;
  }
}
</style>
