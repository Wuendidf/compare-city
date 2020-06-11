<template>
  <section class="page-section bg-light" id="compare">
    <div class="compare">
      <div class="container">
        <div class="text-center">
          <h3 class="section-heading text-uppercase">Compare cost of living between cities:</h3>

          <div class="form-group">
            <form class="form-center">
              <b-form-select v-model="firstCitySelected" class="mb-3">
                <b-form-select-option
                  v-for="item in dataCities"
                  :key="item.id"
                  :value="item.slug"
                  :slug="item.slug"
                >{{item.slug}}</b-form-select-option>
              </b-form-select>
            </form>
            <h2>VS</h2>
            <form class="form-center">
              <b-form-select v-model="secondCitySelected" class="mb-3">
                <b-form-select-option
                  v-for="item in dataCities"
                  :key="item.id"
                  :value="item.slug"
                  :slug="item.slug"
                >{{item.slug}}</b-form-select-option>
              </b-form-select>
            </form>
          </div>
          <button
            class="btn btn-primary btn-m text-uppercase js-scroll-trigger"
            type="submit"
            @click="goComparison"
          >Compare</button>
          <h2>---</h2>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      firstCitySelected: "",
      secondCitySelected: "",
      dataCities: []
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
        this.dataCities = response.data;
        console.log(dataCities);
      } catch (err) {
        console.log("no se conecta a la base de datos");
      }
    },
    async goComparison(item) {
      this.$router.push(`/cities/${this.firstCitySelected}/${this.secondCitySelected}`);
    }
  }
};
</script>
