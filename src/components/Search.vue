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
                v-on:click="submit()"
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


  }),
methods:
 {  submit: function() {

     /*eslint no-console: ["error", { allow: ["log", "error"] }] */
     let search = {title: this.searchTitle, productionFrom: this.searchProductionFrom, productionTo: this.searchProductionTo, cast: this.searchCast}
     this.$emit("inputData", search);

     console.log('Data has been sent.title '+this.searchTitle);


 },


 }

};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
