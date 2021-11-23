<template>
<div class="element-container">

<div class="input-div">
   
  <span>City:</span>
  <input v-model='cityName' type="text" class="address-city">
  <span>State:</span>
  <input v-model='stateName' type="text" class="address-state">
  <span>country:</span>
  <input v-model='countryName' type="text" class="address-country">
  
</div>
  <button v-on:click = 'returnValue' class="submit-button">Submit</button>
</div>


</template>

<style>
input{
  border-radius: 5px;
}
</style>

<script>
import axios from 'axios';

export default {
  data(){
return{
  cityName:'',
  stateName:'', 
  countryName:'',

  latValue:'',
  lngValue:'',

  key: "c7c536d0d6264b3583a7036fdd58e50a", 
  key2: "crVoSZfC4uXoXrwRWmf1BDFGpTnb5Jot",
  hours: "168", 
   


}
  }, 
 created() {
   

      }, 
  methods: {
    returnValue(){
      /* const latitudeValue = this.LatValue;
      const longitudeValue = this.LongValue; */
      const cityName = this.cityName;
      const stateName = this.stateName;
      const countryName = this.countryName;
        if( cityName === ''|| stateName ===''|| countryName ==='' ){
          alert('gimme a number');
        }
        else{
          this.locationGrabber();
           }
      

    },
    locationGrabber(){
      const address = this.returnAddress;
      console.log(address);
         axios
          .get(this.geocodeCallRequest)  // Does a get request
          .then(response => {
            
            this.latValue = response.data.results[0].geometry.lat; 
            this.lngValue = response.data.results[0].geometry.lng;
            
            const latitude = this.latValue; 
            const longitude = this.lngValue;
            
            console.log(latitude);
            console.log(longitude);
            this.changeNameLaterButThisGetsForecasts();
           
            // updates and logs longitude and latitude
          })
          .catch(error => {
            console.log('There was an error:', error.response) 
            // Logs out the error
          })
    },
    changeNameLaterButThisGetsForecasts(){
      axios 
        .get(this.gridIdCallRequest)
        .then(response => {
          const gridID = response.data.properties.gridId;
          const xCoordinate = response.data.properties.gridX;
          const yCoordinate = response.data.properties.gridY;
          console.log(gridID);
          console.log(xCoordinate);
          console.log(yCoordinate);
          console.log('working');
        })
        .catch(error => {
            console.log('There was an error:', error.response) 
            // Logs out the error
          })
          axios
         .get('https://api.weather.gov/gridpoints/TOP/31,80/forecast')
        .then(response =>{
          console.log(response.data.properties.periods);
          console.log('forecast')
        }) 
        .catch(error => {
            console.log('There was an error:', error.response); 
            // Logs out the error
          })
    },
  },
  computed: {
     returnAddress(){
     return this.cityName + ',' + this.stateName + ',' + this.countryName ;
    }, 
    geocodeCallRequest(){
      return 'https://api.opencagedata.com/geocode/v1/json?q=' + this.returnAddress + '&key=' + this.key;
    },
    gridIdCallRequest(){
      return 'https://api.weather.gov/points/' + this.latValue + ','+ this.lngValue;
    }, 

  },
}



/* other api call
    const key2 = 'crVoSZfC4uXoXrwRWmf1BDFGpTnb5Jot';
    const longitude = '-74.1153967';
    const latitude = '40.5685441';
    const hours ='168' ;
    const test2 = async function () {
      try {
        const response2 = await fetch(
          `https://api.weather.gov/gridpoints/TOP/31,80/forecast`
        );
        const data2 = await response2.json();
        console.log(data2.properties.periods);
        console.log('successful 2');
      } catch (error2) {
        console.log(error2);
        alert("something wrong");
      }
    }; 

*/

</script>


