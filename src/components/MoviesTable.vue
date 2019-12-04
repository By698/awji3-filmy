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
    <button @click="checkLimit()">Show more</button>
    <h3>{{limit + '/' + moviesCount}}</h3>
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
    moviesCount: json.valueOf().length,
    sd: NaN
  }),
  methods: {
    checkLimit: function() {
      this.limit += 10;
      if (this.limit > this.moviesCount)
        this.limit = this.moviesCount;
    }
  },
  computed: {
    Movies() {
      return this.limit ? this.showedMovies.slice(0, this.limit) : this.showedMovies;
    },
  },
  watch: {
    searchData: function(){
      let sd = this.searchData
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
      this.moviesCount = this.showedMovies.length;
      if (this.moviesCount < 10) {
        this.limit = this.moviesCount;
      }
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
