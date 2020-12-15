<template>
  <div id="app">
    <Header theTitle = "Current Weather"/>
    <Zipcode @zipcode = "onButtonPress"/>
    <Info v-bind:weatherInfo = "info"/> 
  </div>
</template>

<script>
//Children of App
import Header from './components/Header.vue'
import Zipcode from './components/Zipcode.vue'
import Info from './components/Info.vue'
//Used to get the api call from the website
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Zipcode,
    Info
  },

  data(){
    
    return {
      //placeholder for api call
      info: []
    }
  },

  methods: {
    //Recieves the zip code and temperature from the $emit calls on the Zipcode.vue
      onButtonPress(message, temp){
        //Combines the url
        var url = 'https://api.openweathermap.org/data/2.5/weather?zip=' + message + ',us&units=' + temp + '&appid=d963d2eb8f3c24e2f776dc4a3bbdd660';
        //Gets the information from the api call and sets it to the info
        axios.get(url)
          .then((res) => {
          this.info = res.data;
        })
      }
  },
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
