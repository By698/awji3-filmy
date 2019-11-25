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
        <tr v-for="(movie, index) in Movies" v-bind:key="index">
          <td>{{movie.title}}</td>
          <td>{{movie.year}}</td>
          <td>{{movie.cast.join(", ")}}</td>
          <td>{{movie.genres.join(", ")}}</td>
        </tr>
      </tbody>
    </table>
    <button @click="limit = limit + 10">Show more</button>
  </div>
</template>

<script>
import json from "../assets/movies.json";
import { _ } from "vue-underscore";

export default {
  name: "MoviesTable",
  props:  ['searchData'],
  data: () => ({
    movies: json.valueOf(), // initialize empty array
    limit: 10,
    showedMovies: json.valueOf(),
    sd: NaN
  }),
  computed: {
    Movies() {
      return this.limit ? this.showedMovies.slice(0, this.limit) : this.showedMovies;
    },
      /*eslint no-console: ["error", { allow: ["log", "error"] }] */
    // Arnold() {
    //   console.log(this.searchData)
    //   return _.filter(this.movies, function(movie){
    //     let titleIncludes = movie.title.toLowerCase().includes(this.searchData.title.toLowerCase());
    //     let castIncludes = movie.cast.join().toLowerCase().includes(this.searchData.cast.toLowerCase());
    //     // let yearFrom = movie.year > searchMovie.productionFrom
    //     // let yearTo = movie.year < searchMovie.productionTo
    //     // console.log(castIncludes)
    //     return titleIncludes && castIncludes
    //     })
    // }
  },
  watch: {
    searchData: function(){
      let sd = this.searchData
      console.log(sd)
      this.limit = 10;
      this.showedMovies = _.filter(this.movies, function(movie){
        let titleIncludes = movie.title.toLowerCase().includes(sd.title.toLowerCase());
        let castIncludes = movie.cast.join().toLowerCase().includes(sd.cast.toLowerCase());
        let yearFrom, yearTo;
        if (sd.productionFrom != "")
          yearFrom = movie.year >= sd.productionFrom;
        else
          yearFrom = true;
        if (sd.productionTo != "")
          yearTo = movie.year <= sd.productionTo;
        else
          yearTo = true;
        return titleIncludes && castIncludes && yearFrom && yearTo;
      })
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
