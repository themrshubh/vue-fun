<template>
  <b-container style="padding: 0px">
    <b-row align-h="center">
      <b-col class="chart-container">
        <graph :chartData="chartData" :options="options" />
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
  // data (){
  //   return {
  //     options: {
  //       responsive: true,
  //       maintainAspectRatio: false,
  //       scales: {
  //           xAxes:[{
  //               type:'time',
  //               time:{
  //                 unit: 'month'
  //               }
  //           }],
  //       }
  //     },
  //     chartData: {
  //       labels: [] ,
  //       datasets:[{
  //         label: 'Cases',
  //         data: this.confirmed,
  //       }]
  //     },
  //   }
  // },
  // mounted() {
  //   fetch("https://api.covid19api.com/dayone/country/india", {
  //     method: "GET",
  //     headers:{
  //       Accept: 'application/json'
  //     }
  //   })
  //   .then((response) => {
  //     return response.json()
  //   })
  //   .then((data) => {
  //     this.chartData.labels = data.map(entry => entry.Date)
  //     this.chartData.datasets[0].data = data.map(entry => entry.Confirmed)
  //     this.load = true
  //   })
  // }
}
</script>

<style scoped>
.chart-container{
  position: relative;
  margin: auto;
  width: 30vw;
}
</style>