<template>
  <div>
    <h3>Beer Detail</h3>
    <div v-if="beer">
      <h2>{{beer.name}}</h2>
      <p>Tagline: {{beer.tagline}}</p>
      <p>Description: {{beer.description}}</p>
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