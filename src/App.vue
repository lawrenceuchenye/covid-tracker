<template>
  <Header />
  <div v-if="!loading">
     <DataTitle :title="title" :dataDate="dataDate"/>
     <DataBoxes :stats="status"/>
      <div class="md:flex">
        <CountrySelect @get-country="getCountryData" :countries="countries" />
         <div v-if="status.Country" class="m-4 md:w-2/3">
           <button class="md:w-full  mt-4  md:mt-9 p-3 rounded shadow text-1xl text-white font-bold w-full bg-green-500" @click="clearCountry">Clear Country</button>
         </div>
      </div>
   </div>
  <div v-else>
     <main class="flex justify-center items-center bg-red-600 m-8 p-4 rounded text-white font-bold">
       <h1>Fetching Data</h1>
     </main>
   </div>
</template>

<script> 
  import Header from "./components/Header.vue";
  import DataTitle from "./components/DataTitle.vue";
  import DataBoxes from "./components/DataBoxes.vue";
  import CountrySelect from "./components/CountrySelect.vue";

  export default {
    name: 'App',
    components: {
       Header,
       DataTitle,
       DataBoxes,
       CountrySelect
     },
    data(){
      return {
        loading:true,
        title:"Global",
        status:{},
        dataDate:"",
        countries:[]
      }
    },
    methods:{
      async fetchCovidData(){
        const res=await fetch("https://api.covid19api.com/summary");
        const data=await res.json();
        return data;
      },
      getCountryData(country){
         this.title=country.Country;
         this.status=country;
      },
      async clearCountry(){
         this.loading=true;
         this.title="Global";
         const data=await this.fetchCovidData();
         this.dataDate=data.Date;
         this.status=data.Global;
         this.countries=data.Countries;
         this.loading=false;
      }
    },
    async created(){
      const data=await this.fetchCovidData();
      this.dataDate=data.Date;
      this.status=data.Global;
      this.countries=data.Countries;
      this.loading=false;
    }
  }
</script>

<style scoped>
   
</style>
