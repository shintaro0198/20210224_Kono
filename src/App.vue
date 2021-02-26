<template>
  <div id="app">
    <input type="text" v-model="number">
    <button @click="click">住所自動入力</button>
    <p>Address: {{zip}}</p>
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
       await this.created();
        this.abc()
    },
    async created(){const item = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.number}?apiKey=gpOFMas5ZqJ7LZACnlAnyk0igRdf2Jxlkku5tV6`);
      console.log(item.data)
      const locationData = item.data[0];
      this.number =locationData.postcode;
      this.address=locationData.allAddress;
      console.log(locationData.postcode)
      console.log(locationData)
      console.log(locationData.allAddress)
      console.log(this.address) 
  },
    abc(){
    this.zip=this.address,
      console.log(this.zip)
  }
  
  },
  
}
</script>