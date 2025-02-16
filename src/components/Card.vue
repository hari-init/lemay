<template>
  <div class="card">
    <p class="card-title">{{ cardTitle }}</p>
    <p class="card-value">{{ cardValue }}</p>
    <slot></slot>
  </div>
</template>
<script setup>
defineProps(["cardTitle", "cardValue"]);
</script>
<style scoped>
.card {
  background-color: #232548;
  color: whitesmoke;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 12px;
}

.card-value {
  font-size: 40px;
  color: #11e5ab;
}
</style>
