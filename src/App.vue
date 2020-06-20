<template>
  <div class="container pt-md-3 mb-md-3" style="padding: 0px; margin:auto">
      <b-card class="shadow-card border-0 rounded" no-body>
        <b-tabs class="border-0" pills card>
          <b-tab title="About" active><b-card-text><about /></b-card-text></b-tab>
          <b-tab title="Kanban"><b-card-text><board /></b-card-text></b-tab>
          <b-tab title="Jokes"><b-card-text><dad-jokes /></b-card-text></b-tab>
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
import About from './components/About.vue'

export default {
  name: 'App',
  components: {
    Board,
    DadJokes, 
    Tracker,
    About
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
                },
                gridLines: {
                  color: 'rgba(255, 255, 255, 0.1)',
                },
                scaleLabel:{
                  display:true,
                  labelString:"Date",
                  fontStyle: 'italic',
                  fontColor:'rgba(255, 255, 255, 0.1)'
                }
            }],
            yAxes:[{
              gridLines: {
                color: 'rgba(255, 255, 255, 0.1)',
                zeroLineColor: 'rgba(255, 255, 255, 0.5)'
              },
              scaleLabel:{
                  display:true,
                  labelString:"No. of people",
                  fontStyle: 'italic',
                  fontColor:'rgba(255, 255, 255, 0.1)'
                }
            }]
            
        },
        tooltips: {
          enabled: false
        }
      },
      chartData: {
        labels: [] ,
        datasets:[{
          label: 'Confirmed',
          data: [],
          order:2,
          backgroundColor: 'rgba(255, 0, 93, 0.15)',
          borderColor: 'rgba(255, 0, 93, 1)',
          pointRadius: 0
        },
        {
          label: 'Recovered',
          data: [],
          order: 1,
          backgroundColor: 'rgba(0, 255, 156, 0.15)',
          borderColor: 'rgba(0, 255, 156, 1)',
          pointRadius: 0
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
.tab-content{
  background-color:rgb(12, 12, 12) !important;
}

.card-header{
  background-color:rgb(20, 20, 20) !important;
}

.nav-link.active{
  background-color:rgba(104, 104, 104, 0.336) !important;
}

.nav-link{
  color: rgb(104, 104, 104);
}

.nav-link:hover{
  color: rgb(255, 0, 93)
}

.nav-link:focus{
  outline:0
}

.shadow-card{
  box-shadow: 0 1rem 3rem 0.5rem rgba(0, 0, 0, 0.849) !important;
}
</style>
