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
        <tr v-for="(movie, index) in Filter" v-bind:key="index">
          <td>{{movie.title}}</td>
          <td>{{movie.year}}</td>
          <td>{{movie.cast.join(", ")}}</td>
          <td>{{movie.genres.join(", ")}}</td>
        </tr>
      </tbody>
    </table>
    <button @click="limit = limit + 10">Shore more</button>
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
    Filter() {
           /*eslint no-console: ["error", { allow: ["log", "error"] }] */
      let filtered = _.where(this.movies, {year:2015})
      console.log(filtered)
      return filtered
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
