<template>
<section class="page-section-big">
    <div class="compare">
      <div class="container">
        <div class="text-center">
          <h3 class="section-subheading">Compare cost of living between cities:</h3>
          <div class="row">
            <div class= "col-lg-5 card">
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
            </div>
            <div class= "col-lg-2">
            <h2 class="section-subheading">
              <svg
                class="bi bi-arrow-left-right"
                width="1em"
                height="1em"
                viewBox="0 0 16 16"
                fill="currentColor"
                xmlns="http://www.w3.org/2000/svg"

              >
                <path
                  fill-rule="evenodd"
                  d="M10.146 7.646a.5.5 0 0 1 .708 0l3 3a.5.5 0 0 1 0 .708l-3 3a.5.5 0 0 1-.708-.708L12.793 11l-2.647-2.646a.5.5 0 0 1 0-.708z"
                />
                <path
                  fill-rule="evenodd"
                  d="M2 11a.5.5 0 0 1 .5-.5H13a.5.5 0 0 1 0 1H2.5A.5.5 0 0 1 2 11zm3.854-9.354a.5.5 0 0 1 0 .708L3.207 5l2.647 2.646a.5.5 0 1 1-.708.708l-3-3a.5.5 0 0 1 0-.708l3-3a.5.5 0 0 1 .708 0z"
                />
                <path
                  fill-rule="evenodd"
                  d="M2.5 5a.5.5 0 0 1 .5-.5h10.5a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5z"
                />
              </svg>
            </h2>
            </div>
            <div class= "col-lg-5 card">
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
          <div class= "col-lg-12">
          <button v-if='this.firstCitySelected !== "" && this.secondCitySelected !== ""'
            class="btn btn-primary btn-m text-uppercase js-scroll-trigger"
            type="submit"
            @click="goComparison"
          >Compare</button>
          </div>
          </div>
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
        let response = await this.$axios.get("https://comparecity.herokuapp.com/cities/");
        this.dataCities = response.data;
        console.log(dataCities);
      } catch (err) {
        console.log("no se conecta a la base de datos");
      }
    },
    async goComparison(item) {
      {
        this.$router.push(`/compare/${this.firstCitySelected}&${this.secondCitySelected}`)
    }
    }
  }
};
</script>
