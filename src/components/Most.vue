<template>
  <div>
    <h2>Most Sold Product</h2>
    <ul>
       <li v-for="item in sortedDb" :key="item.id">
        <p>Transaction Date : {{ item.TransactionDate }}</p>
        <p>Recipient : {{ item.Recipient }}</p>
        <p>Item : {{ item.Item }}</p>
        <p>Sales Quantity : {{ item.SalesQuantity }}</p>
        <p>Unit Price (KRW) : {{ item.UnitPrice }}</p>
        <p>Total Value : {{ calculateTotalValue(item) }}원</p>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted, watch } from 'vue';

const searchQuery = ref('');      // 양방향 검색 담을 그릇
const db = ref([]);               // json 값 담을 그릇
// const filteredPosts = ref([]); // 출력 값 담을 그릇
const sortedDb = ref([]);

async function fetchData() {
    db.value = null
        const res = await fetch(
                `https://r1-json-server.fly.dev/db`
                )
        db.value = await res.json()
        sortDbByTotalValue()
}

function calculateTotalValue(item) {
  const totalValue = item.SalesQuantity * item.UnitPrice;
  return totalValue;
}

function sortDbByTotalValue() {
  // totalValue를 기준으로 내림차순 정렬
  sortedDb.value = [...db.value].sort((a, b) => {
    return calculateTotalValue(b) - calculateTotalValue(a);
  });


// 정렬된 배열에 totalValue를 추가하여 화면 갱신 트리거
  sortedDb.value.forEach(item => {
    item.totalValue = calculateTotalValue(item);
  });
}

onMounted(() => {
  fetchData();
});

</script>
