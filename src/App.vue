<template>
  <div id="app">
    <Header @SearchClicked="movieSearched"/>
    <Main :movie="movieToSearch" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";


export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data: function() {
    return {
      movieToSearch: '',
      
    };
  },
  methods: {
    movieSearched: function(movie) {
      this.movieToSearch = movie;  
    },
  },
};
</script>

<style lang="scss">
@import './styles/general.scss'

</style>
