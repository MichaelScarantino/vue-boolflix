<template>

    <div class="single-movie">
        <ul>
            <li>Titolo: {{movieDetails.title}}</li>
            <li>Titolo Originale: {{movieDetails.original_title}}</li>
            <li>Lingua: {{movieDetails.original_language}}</li>
            <li>Voto: {{movieDetails.vote_average}}</li>
        </ul>
    </div>
    
   

   
</template>

<script>
export default {
    name: "SingleMovie",
    data: function() {
        return {
            
        };
    },
    props:{
        movieDetails: Object
    }
}
</script>

<style scoped lang="scss">


.single-movie{

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
        }
    }
}


</style>