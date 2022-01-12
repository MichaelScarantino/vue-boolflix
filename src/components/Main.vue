<template>
    <main>
        
        <div class="container">
            <SingleMovie v-for="movie in movies" :key="movie.id" :movieDetails="movie"/>
        </div>
        
    </main>
</template>

<script>

import SingleMovie from "./SingleMovie.vue";

export default {
    name: "Main",
    components: {
        SingleMovie
    },
    props: {
        movies: Array
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