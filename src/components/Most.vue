<script setup>
import product from "@/assets/product.json";
const products = product

</script>

<template>
  <div>
    <h2>Most Sold Products</h2>
    <ul>
      <li v-for="item in products">
        {{ item.name }} - {{ item.sales }}
      </li>
    </ul>
  </div>
</template>

