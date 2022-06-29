<template>
   <div class="md:flex">
      <div class="bg-blue-200 p-10 rounded m-4 text-center md:w-full">
        <h3 class="font-bold text-4xl text-blue-600">Cases</h3>
         <h4 class="my-4"><span class="text-1xl font-bold">New:</span>{{nwCommas(stats.NewConfirmed)}}</h4>
         <h4 class="my-4"><span class="text-1xl font-bold">Total:</span>{{nwCommas(stats.TotalConfirmed)}}</h4>
      </div>
      <div class="bg-blue-300 p-10 rounded m-4 text-center md:w-full">
        <h3 class="font-bold text-4xl text-blue-600">Deaths</h3>
         <h4 class="my-4"><span class="text-1xl font-bold">New:</span>{{nwCommas(stats.NewDeaths)}}</h4>
         <h4 class="my-4"><span class="text-1xl font-bold">Total:</span>{{nwCommas(stats.TotalDeaths)}}</h4>
      </div>
    </div>
  </template>

<script>
  export default{
   name:"DataBoxes",
   props:{
    stats:Array
   },
    methods:{
     nwCommas(x){
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g,',');
     }
   }
  }
 </script>


<style scoped>
 </style>
