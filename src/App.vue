<script setup>
import Most from './components/Most.vue';

import {ref} from 'vue'

async function jsons() {
        const response = await fetch("http://localhost:3000/db");
        const jsonData = await response.json();
        console.log(jsonData);
}

jsons();

</script>

<template>
  <div>
    <Most />
  </div>
</template>

