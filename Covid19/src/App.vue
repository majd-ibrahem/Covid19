<template>
  <Header />
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate" />

    <DataBoxes :stats="stats" />

    <CountrySelect @getCountry="getCountryData" :countries="countries" />

    <button @click="clearCountryData" v-if="stats.Country"  class="btn-clear">
    Clear Country
    </button>
  </main>

  <main v-else class="wait">
    <p>Fetching Data</p>
    <img :src="loadingImage" alt="">
  </main>
</template>

<script>
import Header from '@/components/Header'
import DataTitle from '@/components/DataTitle'
import DataBoxes from '@/components/DataBoxes'
import CountrySelect from '@/components/CountrySelect'

export default {
  name: 'App',
  components: {
    Header,
    DataTitle,
    DataBoxes,
    CountrySelect,
},
  data(){
    return{
      loading: true,
      title: 'Global',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('./assets/hourglass.gif')
    }
  },
  methods: {
   async fetchCovidData(){
      const result = await fetch(`https://api.covid19api.com/summary`)
      const data = result.json()
      return data
    },
    getCountryData(country){
      this.stats = country
      this.title = country.Country
    },
    async clearCountryData(){
    this.loading = true
    const data = await this.fetchCovidData()
    this.stats = data.Global
    this.title = 'Global'
    this.loading = false
  },
  },

  async created(){
    const data = await this.fetchCovidData()
    
    this.dataDate = data.Date
    this.stats = data.Global
    this.countries = data.Countries
    this.loading = false
  }
}
</script>


<style>
  *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body{
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  }
  .wait{
    width: 200px;
    margin: 0 auto;
    margin-top: 70px;
  }
  .wait p{
    padding: 15px;
    font-size: 1.5rem;
    text-align: center;
  }
  .wait img{
    width: 100px;
    height: 100px;
    display: block;
    margin: 0 auto;
  }

  .btn-clear{
    border: 0;
    outline: 0;
    padding: 10px 15px;
    border-radius: 25px;
    background: rgb(103, 103, 250);
    color: #fff;
    cursor: pointer;
    display: block;
    margin: 0 auto;
    margin-top: 20px;
  }

  .btn-clear:active{
    transform: scale(.95);
    transition: transform .2s;
  }
</style>
