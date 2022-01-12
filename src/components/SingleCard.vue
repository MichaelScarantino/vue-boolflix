<template>
    <div class="single-card">
        <!-- Se l'elemento appartiene a movie, mostra la card con i film -->
        <ul v-if="movieDetails">
            <!-- Se l'immagine è presente nell'elemento inseriscila nella card -->
            <li v-if="movieDetails.backdrop_path"><img :src="`${baseOfHttps}${dimensionImg}${movieDetails.backdrop_path}`" :alt="movieDetails.title"></li>
            <li>Titolo: {{movieDetails.title}}</li>
            <li>Titolo Originale: {{movieDetails.original_title}}</li>
            <li>Lingua: 
                <span v-if="movieDetails.original_language === 'it' || movieDetails.original_language === 'fr' || movieDetails.original_language === 'en'" class="flag">
                    <img :src="require(`../assets/img/${movieDetails.original_language}.jpg`)" :alt="movieDetails.original_language">
                </span>
                <span v-else>
                    {{ movieDetails.original_language }}
                </span>
            </li>
            <li>Voto: 
                <span class="star">
                    <i class="far fa-star"></i>
                    <i class="far fa-star"></i>
                    <i class="far fa-star"></i>
                    <i class="far fa-star"></i>
                    <i class="far fa-star"></i>
                </span> {{Math.round(movieDetails.vote_average / 2)}}</li>
        </ul>

        <!-- Altrimenti mostra la carta con le serie tv-->
        <ul v-else>
            <!-- Se l'immagine è presente nell'elemento inseriscila nella card -->
            <li v-if="serieDetails.backdrop_path"><img :src="`${baseOfHttps}${dimensionImg}${serieDetails.backdrop_path}`" :alt="serieDetails.title"></li>
            <li>Titolo: {{serieDetails.name}}</li>
            <li>Titolo Originale: {{serieDetails.original_name}}</li>
            <li>Lingua: 
                <span v-if="serieDetails.original_language === 'it' || serieDetails.original_language === 'fr' || serieDetails.original_language === 'en'" class="flag">
                    <img :src="require(`../assets/img/${serieDetails.original_language}.jpg`)" :alt="serieDetails.original_language">
                </span>
                <span v-else>
                    {{ serieDetails.original_language }}
                </span>
            </li>
            <li>Voto: 
                <span class="star">
                    <i class="far fa-star"></i>
                    <i class="far fa-star"></i>
                    <i class="far fa-star"></i>
                    <i class="far fa-star"></i>
                    <i class="far fa-star"></i>
                </span> {{Math.round(serieDetails.vote_average / 2)}}</li>
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
        };
    },
    props:{
        movieDetails: Object,
        serieDetails: Object
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