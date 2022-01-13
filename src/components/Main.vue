<template>
    <main>
        <div v-if="movies.length <= 0 || series.length <= 0" class="introduction">
            <h2>Benvenuto, cerca i tuoi Film o le tue Serie Tv preferite.</h2>
        </div>
        <div v-else class="main-content">
            <h2>FILM</h2>
            <div class="main-content-movie-and-series">
                <SingleCard v-for="movie in movies" :key="movie.id" :details="movie" />
            </div>
            <h2>SERIE TV</h2>
            <div class="main-content-movie-and-series">
                <SingleCard v-for="serie in series" :key="serie.id" :details="serie" />
            </div>
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
    height: calc(100% - 80px);
    background-color:rgb(98, 98, 98);
    overflow-y: auto;
    position: relative;
    .introduction{
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        font-size: 35px;
        text-align: center;
    }
    .main-content{
        h2{
        font-size: 30px;
        padding: 30px 20px;
        }
        .main-content-movie-and-series{
            display: flex;
            overflow-x: auto;
            margin: 0 10px;
        }
    }
    
}
</style>