<template>
  <div>
    <h3>Beer Detail</h3>
    <div v-if="beer">
      <h2>{{beer.name}}</h2>
      <p>Tagline: {{beer.tagline}}</p>
      <p>Description: {{beer.description}}</p>
      <p>Ingredients:</p>
      
      <ul v-for="(malt_ingredient, index) in beer.ingredients.malt" :key="index">
        <li>{{malt_ingredient.name}}</li>
      </ul>

      <ul v-for="(hops_ingredient, index) in beer.ingredients.hops" :key="index">
        <li>{{hops_ingredient.name}}</li>
      </ul>

      <ul>
        <li>{{beer.ingredients.yeast}}</li>
      </ul>

    </div>
  </div>
</template>

<script>
import { eventBus } from "../main.js";

export default {
  name: "beer-detail",
  data() {
    return {
      beer: null
    };
  },
  mounted() {
    eventBus.$on("beer-selected", beer => {
      this.beer = beer;
    });
  }
};
</script>

<style>
</style>