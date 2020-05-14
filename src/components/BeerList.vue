<template>
    <div>
        <ul>
            <li v-for="(beer, index) in beers" :beer="beer" :key="index">{{beer.name}}</li>
        </ul>
    </div>
</template>

<script>

export default {
    name: 'beer-list',
    props: ['beers']

}
</script>

<style>

</style>