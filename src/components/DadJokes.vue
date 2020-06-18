<template>
  <b-container style="padding: 0px">
    <b-row align-h="center">
      <b-col cols="8">
        <b-jumbotron>
          <div style="text-align: center">{{joke}}</div>
        </b-jumbotron>
        <b-button @click="getJoke">More!</b-button>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  data(){
    return {
      joke: ''
    }
  },
  mounted() {
    this.getJoke()
  },
  methods: {
      getJoke(){
      fetch("https://icanhazdadjoke.com/", {
        method:'get',
        headers:{
          Accept: 'application/json'
        }
      })
      .then((response) => {
        return response.json()
      })
      .then((data) => {
        this.joke = data.joke
      })
      
    }
  }
}
</script>