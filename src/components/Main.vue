<template>
    <main>
        <template v-if="movie !== ''" class="prova">
            {{callMovieApi(movie)}}
        </template>
        <div class="container">
            <SingleMovie v-for="(movieElement, index) in movieArraySearched" :key="index" :details="movieElement"/>
        </div>
        
    </main>
</template>

<script>
import axios from "axios";
import SingleMovie from "./SingleMovie.vue";

export default {
    name: "Main",
    components: {
        SingleMovie
    },
    props: {
        movie: String
    },
    data: function() {
        return {
            movieArraySearched: [],
        };
    },

    methods: {
        callMovieApi: function(movie) {
            axios.get('https://api.themoviedb.org/3/search/movie',
            {
                params: {
                    api_key: '8a7a082738003c8eafb76274fe038379',
                    query: movie,
                }
            })
            .then((response) => {
                this.movieArraySearched = response.data.results;
            });
        },
    },
}
</script>

<style scoped lang="scss">

main{
    width: 100%;
    
    // TEST
    height: calc(100% - 80px);
    background-color:coral;
    // flex-wrap: wrap;
    overflow-y: auto;

    .container{

        // TEST
        display: flex;
        flex-wrap: wrap;
        width: 70%;
        margin: 20px auto;
    }
}

</style>