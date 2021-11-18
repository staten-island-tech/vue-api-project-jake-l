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
export default {
  data(){
return{
  cityName:'',
  stateName:'', 
  countryName:'',

  address: '',
  latValue:'',
  lngValue:'',


}
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
      console.log(address)
    },
    changeNameLaterButThisGetsForecasts(){
      console.log('still working on this'      )
    },
  },
  computed: {
     returnAddress(){
     return this.cityName + ',' + this.stateName + ',' + this.countryName 
    } 
  },
}
</script>


