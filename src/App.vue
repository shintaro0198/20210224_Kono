<template>
  <div id="app">
    <input type="text" v-model="number">
    <button @click="click">住所自動入力</button>
    <p>Address: {{zip}}</p>
    <p>{{number}}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  mounted() {
    console.log("おはよう");
  },
  data(){
    
    return{
      address:"",
      zip:"",
      number :"",
    }
  },
  methods:{
    click(){
      this.zip=this.address
      
    }
  },
  async created(){
    const item = axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.number}?apikey=gpOFMas5ZqJ7LZACnlAnyk0igRdf2Jxlkku5tV6`)
    const locationData = item.data;
    this.number =locationData.postcode;
    this.address =locationData.allAddress;
    console.log("こんにちは")
    
  },
  abc(){
    console.log("こんばんは")
  }
}
</script>