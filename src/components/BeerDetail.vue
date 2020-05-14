<template>
<div>
    Hello beer detail
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