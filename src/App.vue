<template>
  <div>
    <h1>Beer List</h1>
    <beer-detail />
    <div>
      <beer-list :beers="beers"></beer-list>
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
    // const urls = [
    // "https://api.punkapi.com/v2/beers?page=1&per_page=80",
    // "https://api.punkapi.com/v2/beers?page=2&per_page=80",
    // "https://api.punkapi.com/v2/beers?page=3&per_page=80",
    // "https://api.punkapi.com/v2/beers?page=4&per_page=80"
    // ];

    // const url1 = "https://api.punkapi.com/v2/beers?page=1&per_page=80";
    // url1Clean = fetch(url1).json();
    // const url2 = "https://api.punkapi.com/v2/beers?page=2&per_page=80";
    // url1Clean = fetch(url2).json();
    // const url3 = "https://api.punkapi.com/v2/beers?page=3&per_page=80";
    // url1Clean = fetch(url3).json();
    // const url4 = "https://api.punkapi.com/v2/beers?page=4&per_page=80";
    // url1Clean = fetch(url4).json();
    // this.beers.push(url1)
    // this.beers.push(url2)
    // this.beers.push(url3)
    // this.beers.push(url4)


// fetchData = () => {
//   const urls = [
//     "https://api.punkapi.com/v2/beers?page=1&per_page=80",
//     "https://api.punkapi.com/v2/beers?page=2&per_page=80",
//     "https://api.punkapi.com/v2/beers?page=3&per_page=80",
//     "https://api.punkapi.com/v2/beers?page=4&per_page=80"
//   ];

//   const allRequests = urls.map(url => 
//     fetch(url).then(response => response.json())
//   );

//   console.log("All promises", Promise.all(allRequests));
// };

    fetch("https://api.punkapi.com/v2/beers?page=1&per_page=80")
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