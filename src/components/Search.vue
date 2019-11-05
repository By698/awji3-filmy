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
        />
      </div>
      <div class="form-group row">
        <input type="button" value="Search" class="btn btn-info col-sm-12" />
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "Search"
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
