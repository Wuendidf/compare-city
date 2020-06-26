<template>
  <div class="page-section-big">
  <div class= "page-notfound">
    <div class="container">
      <div class="text-center">
        <h3 class="section-subheading">Ups! Page not found</h3>
        <h1 v-if="error.statusCode === 404"></h1>
        <h1 v-else>An error occurred</h1>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  props: ["error"]
};
</script>
