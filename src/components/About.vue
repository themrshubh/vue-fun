<template>
  <div class="container" style="padding:0px; min-height:60vh">
    <b-row>
      <b-col class="text-center">
        <h2 class="text-muted" style="font-weight: normal"><span class="title">Fun</span> Vue App</h2>
      </b-col>
    </b-row>
    <b-row align-h="center mt-4">
      <b-col class="text-center" cols="md-4">
        <img src="https://media.giphy.com/media/Ahvg1F90pXRQs/giphy-downsized.gif" alt="" style="width:100%">
      </b-col>
    </b-row>
    <b-row align-h="center mt-3">
      <b-col cols="md-6">
        <b-card class="text-muted dark-bg-margin">
          Hello 🥳 <br><br>
          This is a fun little web app that uses various functionalities of Vue.js. 
          It has sub-sections that can be accessed via the tabs above. 
          Each of the above sections is further developed as a component. 
          Every section provides a fun little feature that is independent of the others. 
          I have used <a href="https://vuejs.org/" target="_blank">Vue</a> and <a href="https://getbootstrap.com/" target="_blank">Bootstrap</a> to build and design this web application.
          Find out more about me <a href="https://www.linkedin.com/in/smankar/" target="_blank">here</a>. 
        </b-card>
      </b-col>
    </b-row>
  </div>
</template>

<style>
.title{
  text-align: center; 
  font-weight:normal;
  background: -webkit-linear-gradient(135deg,rgba(0, 225, 255, 0.5), rgba(255, 0, 93, 1));
  background-clip:text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.dark-bg-margin{
  background-color:rgba(50, 50, 50, 0.300) !important;
  margin: 5%
}
</style>