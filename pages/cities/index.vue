<template>
  <section class="page-section bg-light" id="search">
    <div class="container">
      <div class="row">
        <div class="col-lg-12 text-center">
          <h2 class="section-heading text-uppercase">Found your city</h2>
          <h3 class="section-subheading text-muted">select your perfect place.</h3>
        </div>
      </div>

      <form class="form-center">
        <b-form-select v-model="citySelected" class="mb-3">
          <b-form-select-option
            v-for="item in cityCards"
            :key="item.id"
            :value="item.cityName"
          >{{item.cityName}}</b-form-select-option>
        </b-form-select>
      </form>

      <div></div>
      <div class="row">
        <cityCard
          v-for="item in cityFiltered"
          :key="item.id"
          :cityName="item.cityName"
          :image="item.image"
          :country="item.country"
          @click="getDataCity(item)"
          :slug="item.slug"
        ></cityCard>
      </div>
    </div>
  </section>
</template>

<script>
import cityCard from "@/partials/CityCard";


export default {

  data() {
    return {
      citySelected: "all",
      cityCards: [],

    };
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
      } catch (err) {
        console.log("no se conecta");
      }
    },
    async getDataCity(item) {
      this.$router.push(`/cities/${item.slug}`)


    }
  },
  computed: {
    cityFiltered() {
      if (this.citySelected === "all") {
        return this.cityCards;
      }
      return this.cityCards.filter(item => item.cityName === this.citySelected);
    }
  },

  components: {
    cityCard
  }
};
</script>


