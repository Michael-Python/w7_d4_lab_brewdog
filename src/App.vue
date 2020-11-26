<template>
  <div class="body">
    <header class="header">Brewdog API</header>
    <div class="main-container">
      <beers-list :beers='beers'></beers-list>
      <beer-detail :beer='selectedBeer' v-if='selectedBeer'></beer-detail>
    </div>

    <button v-if="!favouriteBeers.includes(selectedBeer)" v-on:click="addToFavourites">Add Beer</button>
    
    <favourite-beers :favouriteBeers="favouriteBeers"></favourite-beers>
  </div>

</template>

<script>
import BeersList from './components/BeersList.vue';
import BeerDetail from './components/BeerDetail.vue';
import FavouriteBeers from './components/FavouriteBeers.vue'
import { eventBus } from './main.js'

export default {
  name: 'app',
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    };
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on("beer-selected", (beer) => {
      this.selectedBeer = beer;
    })
  },
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail,
    "favourite-beers": FavouriteBeers
  },
  methods: {
    addToFavourites: function(){
      this.favouriteBeers.push(this.selectedBeer)
    }

  }
  
}
</script>

<style>
  .main-container {
    display: flex;
    justify-content: space-between;
  }

  body {
    font-family: helvetica;
    margin: 30px
  }

  .header {
    margin: 0px;
    padding: 30px;
    text-align: center;
    background: #09355b;
    color: white;
    font-size: 30px;
}

</style>
