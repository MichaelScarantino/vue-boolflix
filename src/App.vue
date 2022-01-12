<template>
  <div id="app">
    <Header @SearchClicked="movieSearched"/>
    <Main :movies="moviesArray" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import axios from "axios";


export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data: function() {
    return {
      apiKey: '8a7a082738003c8eafb76274fe038379',
      queryValue: '',
      moviesArray: [],
      
    };
  },
  methods: {
    movieSearched: function(search) {
      this.queryValue = search;
      this.callMovieApi();
    },
    callMovieApi: function() {
        axios.get('https://api.themoviedb.org/3/search/movie',
        {
          params: {
            api_key: this.apiKey,
            query: this.queryValue,
          }
        })
        .then((response) => {
          this.moviesArray = response.data.results;
        });
      },
  },
};
</script>

<style lang="scss">
@import './styles/general.scss'

</style>
