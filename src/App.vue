<template>
  <div id="app">
    <input type="text" v-model="number">
    <button @click="click">住所自動入力</button>
    <p>Address: {{zipcode}}</p>
    <p>{{number}}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data(){
    return{
      address:"",
      zipcode:"",
      number :""
    }
  },
  methods:{
    click(){
      this.zipcode=this.address
    }
  },
  async created(){
    const item = axios.get('https://apis.postcode-jp.com/api/v4/postcodes/${zipcode}/td58dzBMRtknZXBqWEARAJ3eVbf0kqTHHbTdBX9')
    const locationData = item.data;
    this.number =locationData.postcodes;
    this.address =location.allAddress
    
  }
}
</script>