<template>
   <div class="flex flex-col items-center  justify-center my-4">
     <h1 class="font-bold text-4xl">{{title}}</h1>
      <h1>{{timeStamp}}</h1>
     </div>
 </template>

<script>
  import moment from "moment"
  export default{
   name:"DataTitle",
   props:{
    title:String,
    dataDate:String
   },
   computed:{
    timeStamp:function(){
     return moment(this.dataDate).format("MMMM Do YY,h:mm:ss a");
    }
   }
  }
 </script>


<style scoped>
 </style>
