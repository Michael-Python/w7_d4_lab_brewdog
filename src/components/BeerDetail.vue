<template>
  <div v-if="beer">
      <h3>{{beer.name}}</h3>
      <p>Tagline: {{beer.tagline}}</p>
      <p>First Brewed: {{beer.first_brewed}}</p>
      <!-- <p>Ingredients: {{beer.ingredients}}</p> -->
      <img class='small-bottle' :src="beer.image_url"/>
  </div>
  <div v-else>
      <p>Please choose a beer</p>
  </div>

</template>

<script>
import { eventBus } from "../main.js";
export default {
    name: 'beer-detail',
    props: ['beer']

}
</script>

<style>
.small-bottle {
    height: 100px
}
</style>