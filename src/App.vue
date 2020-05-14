<template>
  <div>
    <h1>Beer List</h1>
        <div>
            <beer-list :beers='beers'></beer-list>
        </div>
  </div>
</template>

<script>
import BeerList from "./components/BeerList.vue";
import BeerDetail from "./components/BeerDetail.vue";

export default {
  name: "app",
  data() {
    return {
      beers: []
    };
  },
  mounted() {
    fetch("https://api.punkapi.com/v2/beers")
      .then(res => res.json())
      .then(beers => (this.beers = beers));
  },
  components: {
    "beer-list": BeerList,
    "beer-detail": BeerDetail
  }
};
</script>

<style>
</style>