<template>
  <div id="favourite_beers">
      <h2>Favourite Beers</h2>
      <ul>
          <li v-for="favouriteBeer in favouriteBeers">{{favouriteBeer.name}} <img class="small-bottle" :src="favouriteBeer.image_url"/>&nbsp<button style="font-size:24px"> <i class="fa fa-trash"></i></button></li>
      </ul>

  </div>
</template>

<script>
export default {
    name: "favourite_beers",
    props: ['favouriteBeers']
}
</script>

<style scoped>
.small-bottle {
    height: 100px
}
ul {

    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    list-style-type: none;
  }
</style>
