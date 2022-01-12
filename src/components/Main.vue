<template>
    <main>
        <h2>FILM</h2>
        <div class="container">
            <SingleCard v-for="movie in movies" :key="movie.id" :movieDetails="movie" />
        </div>
        <h2>SERIE TV</h2>
        <div class="container">
            <SingleCard v-for="serie in series" :key="serie.id" :serieDetails="serie" />
        </div>
    </main>
</template>

<script>

import SingleCard from "./SingleCard.vue";

export default {
    name: "Main",
    components: {
        SingleCard
    },
    props: {
        movies: Array,
        series: Array
    },
    data: function() {
        return {
           
        };
    },
    methods: {
        
    },
}
</script>

<style scoped lang="scss">

main{
    width: 100%;
    
    // TEST
    height: calc(100% - 80px);
    background-color:coral;
    overflow-y: auto;

    h2{

        // TEST
        padding: 30px 40px;
    }

    .container{

        // TEST
        display: flex;
        flex-wrap: wrap;
        width: 70%;
        margin: 20px auto;

        
    }
}

</style>