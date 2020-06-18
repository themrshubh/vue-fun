<template>
  <div class="container mt-5" style="padding: 0px">
    <b-card no-body>
    <b-tabs pills card>
      <b-tab title="Kanban" active><b-card-text><board /></b-card-text></b-tab>
      <b-tab title="Dad Jokes"><b-card-text><dad-jokes /></b-card-text></b-tab>
      <b-tab title="Tracker" @click="trackerCalled">
        <b-card-text>
          <tracker v-if="this.tracker" :chartData="chartData" :options="options" />
        </b-card-text>
      </b-tab>
    </b-tabs>
  </b-card>
  </div>
</template>

<script>
import Board from './components/Board.vue';
import DadJokes from './components/DadJokes.vue';
import Tracker from './components/Tracker.vue';

export default {
  name: 'App',
  components: {
    Board,
    DadJokes, 
    Tracker
  },
  data (){
    return {
      tracker: false,
      options: {
        responsive: true,
        maintainAspectRatio: false,
        scales: {
            xAxes:[{
                type:'time',
                time:{
                  unit: 'month'
                }
            }],
        }
      },
      chartData: {
        labels: [] ,
        datasets:[{
          label: 'Confirmed',
          data: [],
          order:2
        },
        {
          label: 'Recovered',
          data: [],
          order: 1
        }]
      },
    }
  },
  methods: {
    trackerCalled() {
        this.tracker = true
    }
  },
  mounted(){
    fetch("https://api.covid19api.com/dayone/country/india", {
      method: "GET",
      headers:{
        Accept: 'application/json'
      }
    })
    .then((response) => {
      return response.json()
    })
    .then((data) => {
      this.chartData.labels = data.map(entry => entry.Date)
      this.chartData.datasets[0].data = data.map(entry => entry.Confirmed)
      this.chartData.datasets[1].data = data.map(entry => entry.Recovered)
    })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
