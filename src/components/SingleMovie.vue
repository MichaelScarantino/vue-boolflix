<template>

    <div class="single-movie">
        <ul>
            <li>Titolo: {{details.title}}</li>
            <li>Titolo Originale: {{details.original_title}}</li>
            <li>Lingua: {{details.original_language}}</li>
            <li>Voto: {{details.vote_average}}</li>
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
        details: Object
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