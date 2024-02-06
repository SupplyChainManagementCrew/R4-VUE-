<script setup>
import product from "@/assets/product.json"
const products = product

</script>

<template>
  <div>
    <h2>Most Sold Product</h2>
     <li v-for="item in products">
	    {{ item.name }} - {{ item.sales }} 
     </li>
  </div>
</template>

