<template>
    <div>
        <div>
            <select v-on:change="handleSelect" v-model="selectedBeer">
                <option disabled value="">Select a beer</option>
                <option v-for="(beer, index) in beers" :key="index" :value="beer">{{beer.name}}</option>
            </select>
        </div>

        <h3>Your favourite beers</h3>
        <div v-if="selectedBeer">
            <p>Is this a favourite beer? {{selectedBeer.name}}</p>
            <button v-if="!favBeers.includes(selectedBeer)" v-on:click="addToFav">Add beer to favourites</button>
            <p>Favourite beers list</p>
            <ul>
                <li v-for="(beer, index) in favBeers" :beer="beer" :key="index">{{beer.name}} <button v-on:click="removeFav(beer)">Deselect {{beer.name}}</button></li>
            </ul>
        </div>
        <h3>Full list of beers</h3>
            <ol>
                <li v-for="(beer, index) in beers" :beer="beer" :key="index">{{beer.name}}</li>
            </ol>
    </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'beer-list',
    data(){
        return {
            selectedBeer: {},
            favBeers: []
        }
    },
    props: ['beers'],
    methods: {
        handleSelect(){
            eventBus.$emit('beer-selected', this.selectedBeer)
        },
        addToFav(){
            this.favBeers.push(this.selectedBeer)
        },
        removeFav(beer){
            this.favBeers.splice(this.favBeers.indexOf(beer), 1)
        }
    }

}
</script>

<style>

</style>