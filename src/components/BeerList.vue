<template>
    <div>
        <select v-on:change="handleSelect" v-model="selectedBeer">
            <option disabled value="">Select a beer</option>
            <option v-for="(beer, index) in beers" :key="index" :value="beer">{{beer.name}}</option>
        </select>

    <h3>Full list of beers</h3>
        <ul>
            <li v-for="(beer, index) in beers" :beer="beer" :key="index">{{beer.name}}</li>
        </ul>
    </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'beer-list',
    data(){
        return {
            'selectedBeer': {}
        }
    },
    props: ['beers'],
    methods: {
        handleSelect(){
            eventBus.$emit('beer-selected', this.selectedBeer)
            console.log(this.selectedBeer)
        }
    }

}
</script>

<style>

</style>