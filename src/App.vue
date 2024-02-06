
<template>
  <v-app>
    <v-main>
      <Delivery/>
      <orderinfo/>
      <Most/>
    </v-main>
  </v-app>
</template>

<script>
import Delivery from './components/Delivery.vue'
import orderinfo  from './components/orderInfo.vue'
import Most from './components/Most.vue';
export default {
  name: 'App',
components: {
  Delivery,
  orderinfo,
  Most
}
}
</script>

