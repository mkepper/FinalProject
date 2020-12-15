<template>
    <div class = "textBox">
        <div class="form-group">
            <label for="zip code" class="form-label">Zip Code: </label>
            <input type = "text" class="form-control" v-model = "msg">
        </div>
        <div class="form-group">
            <input class="form-check-input" type="radio" name="temperature" id="fahrenheit" value="F" v-model="temperature" required>
            <label class="form-check-label" for="Fahrenheit">Fahrenheit</label>
            
            <input class="form-check-input" type="radio" name="temperature" id="celsius" value="C" v-model="temperature" required>
            <label class="form-check-label" for="Celcius">Celcius</label>
            <br>
        </div>
        <div class="form-group">
            <button type="button" class="btn btn-primary" v-on:click="checkZip(msg)">Check</button>
        </div>
        <br><br>
    </div>
</template>

<script>
export default {
    name: "TextBox",

    data(){
        return {
            //Stores a placeholder for temperature
            temperature: null
            }
    },

    props: {
        //Placeholder for the zip code
        msg: String,
    },

    methods: {
    checkZip: function(zip) {
        var check = true;
        var temp = "";
        //Checks if the input is 5 digits
        if (zip.length < 5 || zip.length > 5){
            alert("Zip code must be 5 digits")
        }
        else {
            //Validate each character in the zip code entered and make sure they are numbers 
            for (var i = 0; i < zip.length; i++){
                if (zip.charAt(i) == "0" || zip.charAt(i) == "1" || zip.charAt(i) == "2" || zip.charAt(i) == "3" || zip.charAt(i) == "4" || zip.charAt(i) == "5" ||
                zip.charAt(i) == "6" || zip.charAt(i) == "7" || zip.charAt(i) == "8" || zip.charAt(i) == "9" ) {
                    check = true;
                    continue;
                }
                else {
                    //Break out of the loop if any character in the input isn't a number
                    alert("Zip code must only be numbers")
                    check = false;
                    break;
                }
            }
            
            if(this.temperature == "F"){
                temp = "imperial"
                //Run if all inputs are valid and temp is F
                if (check == true){
                    //Uses $emit to pass the zip and temp variables back to the parent App.vue
                this.$emit('zipcode', zip, temp)
                }
            }
            else if(this.temperature == "C"){
                temp = "metric"
                //Run if all inputs are valid and temp is C
                if (check == true){
                    //Uses $emit to pass the zip and temp variables back to the parent App.vue
                this.$emit('zipcode', zip, temp)
                }
            }
            else {
                //Run if neither F or C is selected
                alert("Please select a temperature")
            }
            
        }
    }
  }
}
</script>

<style scoped>
.form-control{
    margin: auto;
    width: 35%;
}

.form-check-label{
    margin-right: 30px;
}

.textBox{
    color: black;
    width: 50%;
    margin: auto;
    padding-top: 20px;
    background-color: gray;
}
</style>