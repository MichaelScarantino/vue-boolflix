<template>
    <div class="single-card">
        <!-- Fronte della carta visibiele al momento della chiamata all' api -->
        <div class="single-card-front">
            <!-- Se l'immagine è presente nell'elemento inseriscila nella card -->
            <div v-if="details.poster_path" class="single-card-img">
                <img :src="`${baseOfHttps}${dimensionImg}${details.poster_path}`" :alt="details.title ? details.title : details.name">
            </div>
            <div v-else class="single-card-title-front">
                <h2>{{details.title ? details.title : details.name}}</h2> 
            </div>
        </div>
        <!-- Retro della carta visibile all'hover -->
        <div class="single-card-back">
            <!-- Se si stampa a schermo un film .title, altrimenti .name -->
            <div class="single-card-title">
                <h3>Titolo:</h3> <span>{{details.title ? details.title : details.name}}</span>
            </div>
            <!-- Se si stampa a schermo un film .original_title, altrimenti .original_name -->
            <div class="single-card-original-title">
                <h3>Titolo Originale:</h3> <span>{{details.original_title ? details.original_title : details.original_name}}</span>
            </div>
            <!-- Se la lingua è presente nell'array flagsArray mostra l' img della bandiera -->
            <div class="single-card-language">
                <h3>Lingua:</h3>  
                <span v-if="flagsArray.includes(details.original_language)" class="flag">
                    <img :src="require(`../assets/img/${details.original_language}.jpg`)" :alt="details.original_language">
                </span>
                <!-- Altrimenti mostra .original_language -->
                <span v-else>
                    {{ details.original_language }}
                </span>
            </div>
            <div class="single-card-vote">
                <h3>Voto:</h3> 
                <span v-for="index in 5" :key="index" class="star">
                    <!-- Se il voto è inferiore al voto ottenuto aggiungi alla stella la classe vote -->
                    <i v-if="index <= Math.round(details.vote_average / 2)" class="fas fa-star vote"></i>
                    <!-- altrimenti aggiungi la stella di default -->
                    <i v-else class="fas fa-star"></i>
                </span>
            </div>
            <div class="single-card-overview">
                <h3>Overview:</h3>
                <span>{{ details.overview }}</span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "SingleCard",
    data: function() {
        return {
            baseOfHttps: 'https://image.tmdb.org/t/p',
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
    height: 513px;
    color: white;
    background-color: rgba(0, 0, 0, 0.8);
    border: 2px solid white;
    margin: 10px;
    flex-shrink: 0;
    cursor: pointer;
    &-front {
        width: 100%;
        height: 100%;
        display: block;
        .single-card-img{
            width: 100%;
            height: 100%;
            img{
                width: 100%;
                height: 100%;
                object-fit: cover;
            }
        }
        .single-card-title-front{
            width: 342px;
            height: 100%;
            padding: 0 10px;
            position: relative;
            background-image: url('../assets/img/no-image.png');
            background-repeat: no-repeat;
            background-size:inherit;
            background-position: center;
            h2{
                text-align: center;
                font-size: 30px;
                padding-top: 20px;
            }
        }
    }
    &-back{
        display: none;
        width: 342px;
        height: 100%;
        padding: 50px 20px;
        overflow-y: auto;
        h3{
            display: inline-block;
            margin-right: 5px;
        }
        span{
            color: rgb(158, 157, 157);
        }
        .single-card-language{

            .flag img{
                width: 25px;
            }
        }
    }
}
.single-card:hover .single-card-front{
        display: none;
    }
.single-card:hover .single-card-back{
    display: block;
}
</style>