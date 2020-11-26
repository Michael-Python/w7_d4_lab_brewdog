<template>
  <div>
      <h3>{{beer.name}}</h3>
      <p>Tagline: {{beer.tagline}}</p>
      <p>First Brewed: {{beer.first_brewed}}</p>
      <img class='image' height=200 :src="beer.image_url"/>
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

</style>