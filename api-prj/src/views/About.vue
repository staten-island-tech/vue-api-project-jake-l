<template>
<div class="input-div">
  <span>Latitude:</span>
  <input v-model='LatValue' type="number" class="latitude-value" >
  <span>Longitude:</span>
  <input v-model='LongValue' type="number" class="longitude-value">
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
  test1: 'data',
  LatValue: '',
  LongValue:'',

}
  }, 
  methods: {
    returnValue(){
      const latitudeValue =this.LatValue;
      const longitudeValue =this.LongValue;
        if( latitudeValue === ''|| longitudeValue===''){
          alert('gimme a number');
        }
        else{
        console.log(latitudeValue);
        console.log(longitudeValue);
        }
  

    },
  },
}
</script>


