<template>
  <div>
    <h1>Beer List</h1>
    <beer-detail />
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
      beers: [],
      beersFav: []
    };
  },
  mounted() {
    fetch("https://api.punkapi.com/v2/beers?page=2&per_page=80")
      .then(res => res.json())
      .then(beers => (this.beers = beers));
  },
  components: {
    "beer-list": BeerList,
    "beer-detail": BeerDetail,
  }
};
</script>

<style>
h1 {
  text-align: center;
  padding: 1rem;
}
.main-container {
  display: flex;
  justify-content: space-around;
  padding: 1rem;
}
</style>