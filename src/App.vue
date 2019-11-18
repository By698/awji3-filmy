<template>
  <div class="container">
    <Search @inputData="updateTitle" />
    <MoviesTable :search-data="searchData" />
    <MoviesByGenre />
    <MoviesByCast />
  </div>
</template>

<script>
import Search from "./components/Search";
import MoviesTable from "./components/MoviesTable";
import MoviesByGenre from "./components/MoviesByGenre";
import MoviesByCast from "./components/MoviesByCast";

export default {
  name: "App",
  components: {
    Search,
    MoviesTable,
    MoviesByGenre,
    MoviesByCast
  },
  data: function() {
    return {
      searchData: {}
    };
  },
  methods: {
    updateTitle(variable) {
      this.searchData = variable;
      /*  eslint no-console: ["error", { allow: ["log", "error"] }] */
      //  console.log(this.searchData);
    },

  }
};
</script>

<style>
</style>
