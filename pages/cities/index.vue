<template>
  <section class="page-section">
    <div class="container">
      <div class="row">
        <div class="col-lg-12 text-center">
          <h3 class="section-subheading">select the city here...</h3>
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
          :votes="votesFiltered(item)"
          :slug="item.slug"
          @click="getDataCity(item)"
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
      cityCards: []
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
        // console.log(this.cityCards)
      } catch (err) {
        console.log("no se conecta a la base de datos");
      }
    },
    async getDataCity(item) {
      this.$router.push(`/cities/${item.slug}`);
    },
    votesFiltered(city) {
      let votes = city.votes.map(item => item === 1);
      votes = votes.reduce((sum,current)=> sum + current)
      return votes

    }
  },
  computed: {
    cityFiltered() {
      if (this.citySelected === "all") {
        return this.cityCards;
      }
      return this.cityCards.filter(item => item.cityName === this.citySelected);
    },

  },
  components: {
    cityCard
  }
};
</script>


