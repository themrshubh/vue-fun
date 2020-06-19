<template>
  <b-container style="padding: 0px; min-height:60vh">
    <b-row>
      <b-col>
        <h3 class="text-muted">Dad Jokes</h3>
        <p class="text-muted">
          dad joke: an unoriginal or unfunny joke of a type supposedly told by middle-aged or older men.
          The component makes use of asynchronous calls and dynamic element loading.
          This pulls new random jokes from an API and displays the joke below. Give it a try!
        </p>
      </b-col>
    </b-row>
    <b-row align-h="center">
      <b-col class="text-center p-1" cols="md-9">
        <b-jumbotron class="jumbo-background mb-5">
          <div class="mb-5">
            <h1 class="joke">{{joke}}</h1>
          </div>
          
          <b-button class="dark-button border-0 shadow-none" @click="getJoke">Not Funny!</b-button>
        </b-jumbotron>
        
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

<style>
.jumbo-background{
  background-color: rgba(20, 20, 20, 0.753) !important;
  margin: 5%
}

.joke{
  text-align: center; 
  font-weight:normal;
  background: -webkit-linear-gradient(135deg,rgba(0, 225, 255, 0.5), rgb(255, 0, 64));
  background-clip:text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

  .dark-button{
    background-color:rgba(104, 104, 104, 0.137) !important;
    color:rgb(199, 199, 199)
  }

  .dark-button:hover{
    background-color: rgba(255, 255, 255, 0.116) !important;
    color:rgb(212, 212, 212)
  }
</style>