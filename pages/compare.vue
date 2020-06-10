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
            v-for="item in dataCity"
            :key="item.id"
            :value="item.cityName"
          >{{item.cityName}}</b-form-select-option>
        </b-form-select>
      </form>
          <h2>VS</h2>
      <form class="form-center">
        <b-form-select v-model="secondCitySelected" class="mb-3">
          <b-form-select-option
            v-for="item in dataCity"
            :key="item.id"
            :value="item.cityName"
          >{{item.cityName}}</b-form-select-option>
        </b-form-select>
      </form>
        </div>
        <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Compare</button>

        <div class="row">
          <div class="col-lg-6 col-sm-8 mb-6">
            <div class="portfolio-item">
              <a class="portfolio-link" data-toggle="modal" href="#portfolioModal1">
                <div class="portfolio-hover">
                  <div class="portfolio-hover-content">
                    <i class="fas fa-plus fa-3x"></i>
                  </div>
                </div>
                <img class="img-fluid" src="assets/img/portfolio/01-thumbnail.jpg" alt />
              </a>
              <div class="portfolio-caption">
                <div class="portfolio-caption-heading">Sevilla</div>
                <div class="portfolio-caption-subheading text-muted">first-City</div>
              </div>
            </div>
          </div>

          <div class="col-lg-6 col-sm-8 mb-6">
            <div class="portfolio-item">
              <a class="portfolio-link" data-toggle="modal" href="#portfolioModal1">
                <div class="portfolio-hover">
                  <div class="portfolio-hover-content">
                    <i class="fas fa-plus fa-3x"></i>
                  </div>
                </div>
                <img class="img-fluid" src="assets/img/portfolio/01-thumbnail.jpg" alt />
              </a>
              <div class="portfolio-caption">
                <div class="portfolio-caption-heading">Sevilla</div>
                <div class="portfolio-caption-subheading text-muted">Second City</div>
              </div>
            </div>
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
      firsDataCity: {},
      secondDataCity: {},
      dataCity: [],

    };
  },
  mounted() {
    this.getCitiesName()
    this.getFirstCity()
  },
  methods: {
    async getCitiesName() {
      let newCityCard = {};

      try {
        let response = await this.$axios.get("http://localhost:8082/cities/");
        console.log(response.data)
        this.dataCity = response.data;
        console.log(dataCity)
      } catch (err) {
        console.log("no se conecta");
      }
    },
    async getFirstCity() {
      try {
        let response = await this.$axios.get(`http://localhost:8082/cities/${firstCitySelected}`);
        console.log(response)

        this.firsDataCity = response.data;
        console.log(firsDataCity)
      } catch (err) {
        console.log("no se conecta");
      }
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
};
</script>
}
</script>
