<template>
  <div class= "card">
    <gmap-map :center="center" :map-type-id="mapTypeId" :zoom="5" style="align-content:center">
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
  max-width: 600px;
  width: 100%;
}
</style>
