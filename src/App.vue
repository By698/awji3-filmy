<template>
  <div class="container">
    <Search @inputData="updateTitle" />
    <MoviesTable />
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
      movie: {

      }
    };
  },
  methods: {
    updateTitle(variable) {
      this.movie= variable;
      /*eslint no-console: ["error", { allow: ["log", "error"] }] */
       console.log(this.movie);
    }
  }
};
</script>

<style>
</style>
