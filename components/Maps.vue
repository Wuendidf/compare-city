<template>
  <div class ="page-section">
    <h1>Google Maps Demo</h1>

    <gmap-map :center="center" :map-type-id="mapTypeId" :zoom="5">
      <gmap-marker
      :position="center"/>
    </gmap-map>
  </div>

</template>

<script>
export default {
  name: "map",
  props: ["center", "mapTypeId"],
  data() {
    return {
      body: ""
    }
  }
};
</script>

<style>
.vue-map-container  {
  height: 460px;
  max-width: 385px;
  width: 100%;
}
</style>
