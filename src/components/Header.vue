<template>
    <header>
        <div class="logo">
            <h2>BOOLFLIX</h2>
        </div>
        <div class="header-search">
            <div class="header-search-input">
                <input v-model="userSearch" type="text" placeholder="Cerca Film o Serie Tv...">
                <span class="search-icon"><i class="fas fa-search"></i></span>
            </div>
            
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
@import '../styles/variables.scss';
header{
    width: 100%;
    height: 80px;
    display: flex;
    align-items: center;
    background-color: black;
    justify-content: center;
    .logo{
        color: $primary_color;
        h2{
            font-size: 40px;
            margin-left: 20px;
        }
    }
    
    .header-search{
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: flex-end;

        &-input{
            width: 30%;
            display: flex;
            align-items: center;
            justify-content: flex-end;
            position: relative;
        }
        input{
            padding: 5px 50px;
            border-radius: 10px;
            width: 100%;
            font-size: 20px;
        }
        .search-icon{
            position: absolute;
            font-size: 20px;
            color: gray;
            left: 15px;
            top: 7px;
        }
        button{
            background-color: $primary_color;
            border: 1px solid $primary_color;
            border-radius: 10px;
            padding: 5px 10px;
            margin: 0 20px;
            font-size: 20px;
        }
        button:hover{
            background-color: rgb(241, 44, 44);
            border: 1px solid rgb(241, 44, 44);
            color: inherit;
        }
    }
    
}
</style>