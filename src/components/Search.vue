<template>
  <div class="search">
    <h1>Search</h1>
    <form>
      <div class="form-group">
        <label for="inputTitle">Title</label>
        <input
          type="text"
          id="inputTitle"
          placeholder="Enter a title or part of a movie title"
          class="form-control"
          v-model="searchTitle"
        />
      </div>
      <div class="form-group row">
        <label for="inputProductionForm" class="col-sm-4 col-form-label">Production year from:</label>
        <div class="col-sm-8">
          <input
            type="text"
            id="inputProductionForm"
            placeholder="Natural number between 1900-2019"
            class="form-control"
            v-model="searchProductionFrom"
          />
        </div>
      </div>
      <div class="form-group row">
        <label for="inputProductionTo" class="col-sm-4 col-form-label">Production year to:</label>
        <div class="col-sm-8">
          <input
            type="text"
            id="inputProductionTo"
            placeholder="Natural number between 1900-2019"
            class="form-control"
            v-model="searchProductionTo"
          />
        </div>
      </div>
      <div class="form-group">
        <label for="inputCast">Cast</label>
        <input
          type="text"
          id="inputCast"
          placeholder="First name and last name"
          class="form-control"
          v-model="searchCast"


        />
      </div>
      <div class="form-group row">
        <input
                type="button"
                value="Search"
                class="btn btn-info col-sm-12"
                v-on:click="updateValues()"
        />
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "Search",

  data: () => ({
    //storing from input right here, right now
    searchTitle: "",
    searchProductionFrom: "",
    searchProductionTo: "",
    searchCast: "",
    //storing after clicking button
    title: "",
    productionFrom: "",
    productionTo: "",
    cast: "",

  }),
methods:
 {  updateValues: function() {
    this.title = this.searchTitle;
    this.productionFrom = this.searchProductionFrom;
    this.productionTo = this.searchProductionTo;
    this.cast = this.searchCast;
     /*eslint no-console: ["error", { allow: ["log", "error"] }] */

     console.log(this.title);
     console.log(this.productionFrom);
     console.log(this.productionTo);
     console.log(this.cast);

 },


 }

};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
