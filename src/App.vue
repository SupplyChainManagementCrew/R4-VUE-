<template>
  <v-app>
    <v-main>
      <div class="split-container">
        <!-- 왼쪽 영역 -->
        <div class="left-section">
          <Delivery/>
          <orderinfo/>
        </div>

        <!-- 오른쪽 영역 -->
        <div class="right-section">
          <Most/>
          <graphMs/>
          <Comparison />
        </div>
      </div>
    </v-main>
  </v-app>
</template>

<script>
import Delivery from './components/Delivery.vue'
import orderinfo from './components/orderInfo.vue'
import Most from './components/Most.vue';
import graphMs from './components/graph-ms.vue'
import Comparison from './components/Comparison.vue'

export default {
  name: 'App',
  components: {
    Delivery,
    orderinfo,
    Most,
    graphMs,
    Comparison
  }
}
</script>

<style scoped>
/* 스타일 추가 */
.split-container {
  display: flex; /* 플렉스 컨테이너로 설정 */
}

.left-section {
  width: 1500px; /* 왼쪽 영역의 너비 설정 */
  height: 100%; /* 컨테이너 높이에 맞춤 */
  border: 1px solid red;
}

.right-section {
  flex-grow: 1; /* 오른쪽 영역이 남은 공간을 모두 차지하도록 설정 */
  height: 100%;
  display: flex; /* 플렉스 컨테이너로 설정 */
  flex-direction: column; /* 수직 방향으로 정렬 */
}

/* 오른쪽 영역 내의 각 컴포넌트 스타일 */
.right-component {
  flex-grow: 1;
  border: 1px solid green;
  margin-bottom: 10px; /* 각 컴포넌트 사이에 간격을 줌 */
}
</style>