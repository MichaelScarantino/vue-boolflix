<template>
    <header>
        <div class="header-search">
            <input v-model="userSearch" type="text">
            <button @click="$emit('SearchClicked', userSearch)">Cerca</button>
        </div>
    </header>
</template>

<script>
export default {
    name: "Header",
    data: function() {
        return {
            userSearch: '',
        };
    },
}
</script>

<style scoped lang="scss">

header{
    width: 100%;
    
    // TEST
    height: 80px;
    display: flex;
    align-items: center;
    background-color: cyan;
    justify-content: center;

    .header-search{

        // TEST
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;

        input{

            // TEST
            width: 50%;
            font-size: 20px;
        }

        button{
            
            // TEST
            padding: 5px 10px;
            margin-left: 20px;
        }
    }
    
    
    

    
    
    
}

</style>