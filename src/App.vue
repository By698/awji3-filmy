<template>
  <div class="container">
    <Search />
    <MoviesTable/>
    <MoviesByGenre/>
    <MoviesByCast/>
  </div>
</template>

<script>
import Search from "./components/Search";
import MoviesTable from "./components/MoviesTable"
import MoviesByGenre from './components/MoviesByGenre'
import MoviesByCast from './components/MoviesByCast'

export default {
  name: "app",
  components: {
    Search,
    MoviesTable,
    MoviesByGenre,
    MoviesByCast
  }
};
</script>

<style>
</style>
