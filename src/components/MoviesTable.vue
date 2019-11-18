<template>
  <div class="table-movies">
    <table class="table-condensed table-hover">
      <thead>
        <tr>
          <th>Title</th>
          <th>Production Year</th>
          <th>Cast</th>
          <th>Genres</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(movie, index) in Arnold" v-bind:key="index">
          <td>{{movie.title}}</td>
          <td>{{movie.year}}</td>
          <td>{{movie.cast.join(", ")}}</td>
          <td>{{movie.genres.join(", ")}}</td>
        </tr>
      </tbody>
    </table>
    <!-- <button @click="limit = limit + 10">Shore more</button> -->
  </div>
</template>

<script>
import json from "../assets/movies.json";
import { _ } from "vue-underscore";

export default {
  name: "MoviesTable",
  data: () => ({
    movies: json.valueOf(), // initialize empty array
    limit: 10
  }),
  computed: {
    Movies() {
      return this.limit ? this.movies.slice(0, this.limit) : this.movies;
    },
      /*eslint no-console: ["error", { allow: ["log", "error"] }] */
    Arnold() {
      console.log(this.movieFromApp)
      let sm = this.searchMovie
      return _.filter(this.movies, function(movie){
        let titleIncludes = movie.title.toLowerCase().includes(sm.title);
        let castIncludes = movie.cast.join().toLowerCase().includes(sm.cast);
        // let yearFrom = movie.year > searchMovie.productionFrom
        // let yearTo = movie.year < searchMovie.productionTo
        // console.log(castIncludes)
        return titleIncludes && castIncludes
        })
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
