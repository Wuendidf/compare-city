<template>
  <div>
    <MainSlider image="/assets/imgheader-bg.jpg/" size="small"/>

  <nuxt />

  </div>
</template>

<script>
import search from "@/pages/cities";
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




