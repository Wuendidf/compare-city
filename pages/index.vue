<template>
  <div>
    <MainSlider image="/assets/imgheader-bg.jpg/" size="small"/>

    <search></search>
  <nuxt />
    <compare></compare>

  </div>
</template>

<script>
import search from "@/pages/search";
import MainSlider from "@/components/MainSlider";
import compare from "@/pages/compare"



export default {
  components: {
    MainSlider,
    search,
    compare,

  }
};
</script>




