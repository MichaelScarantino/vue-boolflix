<template>
  <div id="app">
    <Header @SearchClicked="movieSearched"/>
    <Main :movies="moviesArray" :series="seriesArray" />
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
      getHttps: 'https://api.themoviedb.org/3/search',
      apiKey: '8a7a082738003c8eafb76274fe038379',
      queryValue: '',
      moviesArray: [],
      seriesArray:[],
      
    };
  },
  methods: {
    // Funzione che riceve l'emit da Header.vue:
      // attribuisce l'emit ricevuto ad una variabile queryValue nei data,
      // richiama le variabili callMoviesApi e callSeriesApi
    movieSearched: function(search) {
      this.queryValue = search;
      this.callMoviesApi();
      this.callSeriesApi();
    },
    // Funzione che richiama l'api dei movie ricevendo i parametri dai data
    callMoviesApi: function() {
      axios.get(`${this.getHttps}/movie`,
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

    // Funzione che richiama l'api delle serie ricevendo i parametri dai data
    callSeriesApi: function() {
      axios.get(`${this.getHttps}/tv`,
      {
        params: {
          api_key: this.apiKey,
          query: this.queryValue,
        }
      })
      .then((response) => {
        this.seriesArray = response.data.results;
      });
    },
  },
};
</script>

<style lang="scss">
@import './styles/general.scss'

</style>
