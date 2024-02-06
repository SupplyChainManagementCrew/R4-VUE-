<template>
  <div>
    <h2>Most Sold Product</h2>
    <ul>
       <li v-for="item in sortedDb" :key="item.id">
        <p>거래일 : {{ item.TransactionDate }}</p>
        <p>수령인 : {{ item.Recipient }}</p>
        <p>제품명 : {{ item.Item }}</p>
        <p>주문번호 : {{item.id}}</p>
        <p>수    량 : {{ item.SalesQuantity }}개</p>
        <p>단    가 : {{ item.UnitPrice }}원</p>
        <p>공급가 : {{ calculateTotalValue(item) }}원</p>
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
