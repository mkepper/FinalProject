<template>
    <div class = "weather">
        <!--Displays the temperature, city, weather type, and image based on the api call-->
        <h3>Temperature: {{weatherInfo.main.temp}}</h3>
        <h3>City: {{weatherInfo.name}}</h3>
        <h3>{{weatherInfo.weather[0].main}}</h3>
        <img v-bind:src="getImageUrl(weatherInfo.weather[0].icon)">
    </div>
</template>

<script>
export default {
    name: "WeatherInfo",
    props: ['weatherInfo'],
    methods: {
        //Gets the url path for the image
        getImageUrl: function(id){
            var url = "http://openweathermap.org/img/wn/"
            //Combines the url path
            return url + id + "@2x.png"
        }
    }
}
</script>

<style scoped>
.weather{
    background-color: gray;
    color: black;
    width: 50%;
    margin: auto;
}
</style>

