<script setup>

import { ref, onMounted } from 'vue';

const products = ref([]);

const mostSoldProduct = ref({ name: '', sales: 0 });

onMounted(() => {
  fetch('@/assets/products.json')
    .then(response => response.json())
    .then(data => {
      products.value = data;
      updateMostSoldProduct();
    });
});

function updateMostSoldProduct() {
  mostSoldProduct.value = products.value.reduce(
    (prev, current) => (prev.sales > current.sales ? prev : current),
    {}
  );
}
</script>

<template>
  <div>
    <h2>Most Sold Product</h2>
    <p>{{ mostSoldProduct.name }} - {{ mostSoldProduct.sales }} units</p>
  </div>
</template>

