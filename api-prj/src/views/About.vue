<template>
<div class="input-div">
 <!--  <span>Latitude:</span>
  <input v-model='LatValue' type="number" class="latitude-value" >
  <span>Longitude:</span>
  <input v-model='LongValue' type="number" class="longitude-value"> -->
  
  <span>City:</span>
  <input v-model='cityName' type="text" class="address-city">
  <span>State:</span>
  <input v-model='stateName' type="text" class="address-state">
  <span>country:</span>
  <input v-model='countryName' type="text" class="address-country">
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

  LatValue: '',
  LongValue:'',

}
  }, 
  methods: {
    returnValue(){
      const latitudeValue = this.LatValue;
      const longitudeValue = this.LongValue;
        if( latitudeValue === ''|| longitudeValue===''){
          alert('gimme a number');
        }
        else{
        console.log(latitudeValue);
        console.log(longitudeValue);
        }
  

    },
  },
  computed: {
    returnAddress(){
//working on this. maybe add a method that calls this?
    }
  },
}
</script>


