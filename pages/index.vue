<template>
  <div>
    <MainSlider class="img-fluid" image="/assets/img/header-bg.jpg" size="small"/>

  <nuxt />

  </div>
</template>

<script>
import search from "@/pages/cities";
import MainSlider from "@/components/MainSlider";
import compare from "@/pages/compare/index"



export default {
  components: {
    MainSlider,
    search,
    compare,

  }
};
</script>




