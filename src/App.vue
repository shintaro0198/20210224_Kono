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
    console.log(this.item)
  },
  data(){
    
    return{
      address:"",
      zip:"",
      number :"",
    }
  },
  methods:{
    async click(){
      const item = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.number}?apiKey=gpOFMas5ZqJ7LZACnlAnyk0igRdf2Jxlkku5tV6`);
      console.log(item)
      const locationData = item.data;
      this.number =locationData.postcode;
      locationData.allAddress=this.address;
      console.log(locationData.postcode)
      console.log(this.address)
      return this.zip=this.address
    }
  },
  async created(){
    
    
  },
  abc(){
    console.log("こんばんは")
  }
}
</script>