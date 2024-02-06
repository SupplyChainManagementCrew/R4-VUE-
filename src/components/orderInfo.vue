<script setup>
import { ref, onMounted } from 'vue'

const jsonData = ref([])

async function fetchData() {
  try {
    const response = await fetch("http://localhost:3000/db");
    jsonData.value = await response.json();
    console.log(jsonData.value);
  } catch (error) {
    console.error("Error fetching data:", error);
  }
}

onMounted(() => {
  fetchData();
})
</script>

<template>
  <div>
    <p v-for="item in jsonData" :key="item.id">
      {{ item }}
    </p>
  </div>
</template>

