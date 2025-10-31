<script setup>
import Stat from "./components/Stat.vue";
import CitySelect from "./components/CitySelect.vue";
import { computed, ref } from "vue";
let savedCity = ref("New York");
let data = ref({
  humidity: 90,
});

const dataModified = computed((prev) => {
  console.log("Computing modified data", prev);
  return {
    label: "Humidity",
    stat: data.value.humidity + "%",
  };
});

async function getCity(city) {
  savedCity.value = city;
  data.value.humidity = 20;
}
</script>

<template>
  <main class="main">
    <div id="city">{{ savedCity }}</div>
    <Stat v-bind="dataModified" />
    <Stat label="Weather" stat="0%" />
    <CitySelect @select-city="getCity" />
  </main>
</template>

<style scoped>
.main {
  background: var(--color-bg-main);
  padding: 60px 50px;
  border-radius: 25px;
}
</style>
