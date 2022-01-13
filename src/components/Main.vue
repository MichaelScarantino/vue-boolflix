<template>
    <main>
        <h2>FILM</h2>
        <div class="container">
            <SingleCard v-for="movie in movies" :key="movie.id" :details="movie" />
        </div>
        <h2>SERIE TV</h2>
        <div class="container">
            <SingleCard v-for="serie in series" :key="serie.id" :details="serie" />
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
    background-color:rgb(98, 98, 98);
    overflow-y: auto;

    h2{
        font-size: 40px;
        // TEST
        padding: 30px 20px;
    }

    .container{
        display: flex;
        overflow-x: auto;
        margin: 0 10px;
    }
}

</style>