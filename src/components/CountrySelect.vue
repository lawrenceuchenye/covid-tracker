
<template>
  <div class="m-4">
     <select @change="onChange" v-model="selected" class="form-select mt-5 block shadow md:mt-10 border rounded p-3 w-full">
        <option v-for="country in countries" :value="country.ID">{{country.Country}}</option>
     </select>
   </div>
 </template>

<script>
  export default{
    name:"CountrySelect",
    props:["countries"],
    data(){
      return{
        selected:0
      }
    },
    methods:{
     onChange(){
       const country=this.countries.find((item)=>item.ID === this.selected);
       this.$emit("get-country",country);
     }
    }
  }
</script>

<style scoped>
 </style>
