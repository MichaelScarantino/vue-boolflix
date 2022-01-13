<template>
    <div class="single-card">
        <ul>
            <!-- Se l'immagine è presente nell'elemento inseriscila nella card -->
            <li v-if="details.backdrop_path"><img :src="`${baseOfHttps}${dimensionImg}${details.backdrop_path}`" :alt="details.title ? details.title : details.name"></li>
            <!-- Se si stampa a schermo un film .title, altrimenti .name -->
            <li>Titolo: {{details.title ? details.title : details.name}}</li>
            <!-- Se si stampa a schermo un film .original_title, altrimenti .original_name -->
            <li>Titolo Originale: {{details.original_title ? details.original_title : details.original_name}}</li>
            <!-- Se la lingua è presente nell'array flagsArray mostra l' img della bandiera -->
            <li>Lingua: 
                <span v-if="flagsArray.includes(details.original_language)" class="flag">
                    <img :src="require(`../assets/img/${details.original_language}.jpg`)" :alt="details.original_language">
                </span>
                <!-- Altrimenti mostra .original_language -->
                <span v-else>
                    {{ details.original_language }}
                </span>
            </li>
            <li>Voto: 
                <span v-for="index in 5" :key="index" class="star">
                    <!-- Se il voto è inferiore al voto ottenuto aggiungi alla stella la classe vote -->
                    <i v-if="index <= Math.round(details.vote_average / 2)" class="fas fa-star vote"></i>
                    <!-- altrimenti aggiungi la stella di default -->
                    <i v-else class="fas fa-star"></i>
                </span>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "SingleCard",
    data: function() {
        return {
            baseOfHttps: 'https://image.tmdb.org/t/p/',
            dimensionImg: '/w342',
            flagsArray: ['it', 'en', 'fr']
        };
    },
    props:{
        details: Object,
    },
    methods: {
        
    }
}
</script>

<style scoped lang="scss">


.single-card{

    // TEST
    width: calc((100% / 4) - 20px);
    padding: 20px;
    margin: 10px;
    border: 1px solid red;

    ul{

        // TEST
        list-style-type: none;

        li{

            // TEST
            padding: 5px;

            .flag img{
                width: 25px;
                vertical-align: middle;
            }
        }
    }
}


</style>