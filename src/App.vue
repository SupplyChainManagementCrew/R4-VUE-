<template>
  <v-app>
    <v-main>
      <v-container fluid>
        <v-row>
          <v-col>
            <v-card>
              <v-card-title>Delivery</v-card-title>
              <v-card-text>
                <Delivery />
              </v-card-text>
            </v-card>
          </v-col>
          <v-col>
            <v-card>
              <v-card-title>Order Info</v-card-title>
              <v-card-text>
                <orderinfo />
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-col>
            <v-card>
              <v-card-title>Most Sold Product</v-card-title>
              <v-card-text>
                <Most />
              </v-card-text>
            </v-card>
          </v-col>
          <v-col>
            <v-card>
              <v-card-title>Graph</v-card-title>
              <v-card-text>
                <graphMs />
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-col>
            <v-card>
              <v-card-title>Comparison</v-card-title>
              <v-card-text>
                <Comparison />
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>


<script>
import Delivery from './components/Delivery.vue'
import orderinfo  from './components/orderInfo.vue'
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
