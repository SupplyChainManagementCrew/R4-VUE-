<template> 
       <li v-for="item in graph">
        <p>Date: {{ item.date }}</p>
        <p>Revenue: {{ item.revenue }}</p>
        <p>Sales Quantity: {{ item.sales_quantity }}</p>
        <p>Recipient: {{ item.recipient }}</p>
        <p>{{item}}</p>
      </li>
</template>


<script setup>
import { ref, onMounted, watch } from 'vue';
// import axios from 'axios';

const searchQuery = ref(''); //양방향 검색 담을 그릇
const graph = ref([]); // json 값 담을 그릇
// const filteredPosts = ref([]); // 출력 값 담을 그릇

async function fetchData() {
    graph.value = null
        const res = await fetch(
                `https://r1-json-server.fly.dev/graph`
                )
        graph.value = await res.json()
}

// const filterPosts = () => {
//   if (searchQuery.value) {
//     filteredPosts.value = posts.value.filter(post => post.recipient_address .includes(searchQuery.value));
//   } else {
//     filteredPosts.value = posts.value;
//   }
// };

onMounted(() => {
  fetchData();
});

</script>