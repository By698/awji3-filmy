<template>
  <div class="movies-by-genre">
    <h1>Movies by genre</h1>
    <select
      class="col-sm-4"
      v-model="selected"
      :searchable="true"
      :clearable="true"
      :filterable="true"
      :close-on-select="true"
    >
      <option :value="null" disabled hidden>Select genre</option>
      <option v-for="(genre) in UniqueGenres" :key="genre">{{genre}}</option>
    </select>
    <ol>
      <li v-for="(movie, index) in SelectedGenreMovies" :key="index">{{movie.title}}</li>
    </ol>
  </div>
</template>

<script>
import json from "../assets/movies.json";
import { _ } from "vue-underscore";

export default {
  name: "MoviesByGenre",
  data: () => ({
    movies: json.valueOf(),
    selected: null
  }),
  computed: {
    UniqueGenres() {
      let genres = _.map(this.movies, function(movie) {
        return movie.genres;
      });
      genres = _.flatten(genres);
      let uniqueGenres = _.unique(genres);
      return uniqueGenres.sort();
    },
    SelectedGenreMovies() {
      
      if(this.selected != null){
        let sa = this.selected;
        let selectedGenreMovies = _.filter(this.movies, function(movie){
          return movie.genres.join().includes(sa);
        })
        return selectedGenreMovies;
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
