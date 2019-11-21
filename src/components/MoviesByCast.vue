<template>
  <div class="movies-by-cast">
    <h1>Movies by cast</h1>
    <select v-model="selected"  :searchable="true"  :clearable="true" :filterable="true"  :close-on-select="true"
    >
      <option v-for="(artist) in UniqueCast" v-bind:key="artist">{{artist}}</option>
    </select>
  </div>
</template>

<script>
  import json from '../assets/movies.json';
 import {_} from 'vue-underscore'

  export default {
  name: "MoviesByCast",
  data: () => ({
   movies: json.valueOf(), // initialize empty array
    // cast:
 }),
  computed: {
    UniqueCast() {
     let actors = _.map(this.movies, function(movie){
       return movie.cast;
     });
     actors = _.flatten(actors);
      let cast= _.unique(actors);
      return cast;
    }

  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
