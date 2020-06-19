<template>
  <b-container style="padding: 0px; min-height:60vh">
    <b-row>
      <b-col>
        <h3 class="text-muted">COVID-19 Tracker</h3>
        <p class="text-muted">
          Coronavirus disease (COVID-19) is an infectious disease caused by a newly discovered coronavirus. 
          This component uses JavaScript to make API calls and plots a graph based on the requested attributes.
          This showcases the use of prop-chaining and dynamic component loading.
        </p>
      </b-col>
    </b-row>
    <b-row align-h="center">
      <b-col cols="md-8">
        <b-card class="dark-bg mt-3" no-body><graph style="padding: 0px; margin:0px" :chartData="chartData" :options="options" /></b-card>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import Graph from './Graph.vue'

export default {
  components:{
    Graph
  },
  props:['chartData', 'options'],
}
</script>

<style>
.dark-bg{
  background-color: rgba(20, 20, 20, 0.753) !important;
  margin:0px
}

.graph-subtitle{
  color: rgb(255, 0, 93)
}

</style>