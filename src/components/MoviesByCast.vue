<template>
  <div class="movies-by-cast">
    <h1>Movies by cast</h1>
    <select
      class="col-sm-4"
      v-model="selected"
      :searchable="true"
      :clearable="true"
      :filterable="true"
      :close-on-select="true"
    >
      <option :value="null" disabled hidden>Select actor</option>
      <option v-for="(artist) in UniqueCast" :key="artist">{{artist}}</option>
    </select>
    <ol>
      <li v-for="(movie, index) in SelectedActorMovies" :key="index">{{movie.title}}</li>
    </ol>
  </div>
</template>

<script>
import json from "../assets/movies.json";
import { _ } from "vue-underscore";

export default {
  name: "MoviesByCast",
  data: () => ({
    movies: json.valueOf(),
    selected: null
  }),
  computed: {
    UniqueCast() {
      /*eslint no-console: ["error", { allow: ["log", "error"] }] */
      // console.log(this.movies)
      let actors = _.map(this.movies, function(movie) {
        return movie.cast;
      });
      actors = _.flatten(actors);

      let cast = _.unique(actors);
      return cast;
    },
    SelectedActorMovies() {
      
      if(this.selected != null){
        let sa = this.selected;
        let selectedActorMovies = _.filter(this.movies, function(movie){
          return movie.cast.join().includes(sa);
        })
        return selectedActorMovies;
      } else {
        return [];
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
