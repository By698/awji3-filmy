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
        <tr v-for="movie in movies" v-bind:key="movie.title">
          <td>{{movie.title}}</td>
          <td>{{movie.year}}</td>
          <td>{{movie.cast}}</td>
          <td>{{movie.genres}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
 import json from '../assets/movies.json'

export default {
  name: "MoviesTable",
  data: () => ({
    movies: json.valueOf() // initialize empty array
  })
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
