<template>
  <div>
    <h1>Brewdog API</h1>
    <div class="main-container">
      <beers-list :beers='beers'></beers-list>
      <beer-detail :beer='selectedBeer' v-if='selectedBeer'></beer-detail>
    </div>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue';
import BeerDetail from './components/BeerDetail.vue';
import { eventBus } from './main.js'

export default {
  name: 'app',
  data(){
    return {
      beers: [],
      selectedBeer: null
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
    "beer-detail": BeerDetail
  }
}
</script>

<style>
  .main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
