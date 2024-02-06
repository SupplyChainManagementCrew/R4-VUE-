<template>
  <v-app>
    <v-main>
      <Delivery/>
    </v-main>
  </v-app>
</template>

<script>
import Delivery from './components/Delivery.vue'

export default {
  name: 'App',
components: {
  Delivery
}
}
</script>
