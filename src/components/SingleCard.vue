<template>
    <div class="single-card">
        <!-- Se l'elemento appartiene a movie, mostra la card con i film -->
        <ul v-if="movieDetails">
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
            <li>Voto: {{movieDetails.vote_average}}</li>
        </ul>

        <!-- Altrimenti mostra la carta con le serie tv-->
        <ul v-else>
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
            <li>Voto: {{serieDetails.vote_average}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "SingleCard",
    data: function() {
        return {
            
        };
    },
    props:{
        movieDetails: Object,
        serieDetails: Object
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