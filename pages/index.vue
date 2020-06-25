<template>
  <div class="page-index">
    <MainSlider />

    <nuxt />
  </div>
</template>

<script>
import MainSlider from "@/components/MainSlider";

export default {
  data() {
    return {
      cityCards: []
    };
  },
  components: {
    MainSlider
  },
  mounted() {
    this.getAllCities();
  },
  methods: {
    async getAllCities() {
      let newCityCard = {};

      try {
        let response = await this.$axios.get("http://localhost:8082/cities/");
        this.cityCards = response.data;
        console.log(this.cityCards);
      } catch (err) {
        console.log("no se conecta a la base de datos");
      }
    }
  }
};
</script>




