<template>
  <section class="page-section bg-light">
    <div class="container">
      <img class="img-fluid d-block mx-auto" src="#" alt />
      <div class="row justify-content-center">
        <div class="col-lg-12">
          <h2 class="text-uppercase">{{cityData.cityName}}</h2>
          <span>Weather</span>
          <span>Humidity</span>
        </div>
      </div>
      <div class="row justify-content-center">
        <div class="col-lg-6">
          <h3>Generals</h3>
          <table class="table" id="table-1">
            <tbody>
              <tr>
                <th scope="row">Region</th>
                <td scope="col">{{}}</td>
              </tr>
              <tr>
                <th scope="row">Country</th>
                <td>{{}}</td>
              </tr>
              <tr>
                <th scope="row">Currency</th>
                <td>{{}}</td>
              </tr>
              <tr>
                <th scope="row">Population</th>
                <td>{{}}</td>
              </tr>
              <tr>
                <th scope="row">Weather</th>
                <td>{{}}</td>
              </tr>
              <tr>
                <th scope="row">Humidity</th>
                <td>{{}}</td>
              </tr>
            </tbody>
          </table>
        </div>
        <div class="col-lg-6">
          <h3>Quality of life(score)</h3>
          <table class="table" id="table-2">
            <tbody>
              <tr>
                <th scope="row">Segurity</th>
                <td scope="col">{{}}</td>
              </tr>
              <tr>
                <th scope="row">Fun</th>
                <td>{{}}</td>
              </tr>
              <tr>
                <th scope="row">Quality of hospitals</th>
                <td>{{}}</td>
              </tr>
              <tr>
                <th scope="row">Friendly to foreigners</th>
                <td>{{}}</td>
              </tr>
              <tr>
                <th scope="row">Level of education</th>
                <td>{{}}</td>
              </tr>
              <tr>
                <th scope="row">Tolerance (racial)</th>
                <td>{{}}</td>
              </tr>
              <tr>
                <th scope="row">Friendly enviromental</th>
                <td>{{}}</td>
              </tr>
              <tr>
                <th scope="row">Job opportunities</th>
                <td>{{}}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>

      <div class></div>
      <youtube class video-id="c_-kO8qrqB4"></youtube>
    </div>
  </section>
</template>

<script>
import cityCard from "@/partials/CityCard";

export default {
  data() {
    return {
      currentSlug: this.$route.params.slug,
      cityData: {}
    };
  },
  mounted() {
    this.setDataCity();
  },
  methods: {
    async setDataCity() {
      let newCitychacha = {};
      try {
        let response = await this.$axios.get(
          `http://localhost:8082/cities/${this.currentSlug}`
        );
        console.log(response.data);
        this.cityData = response.data;
        console.log(cityData);
      } catch (err) {
        console.log(err.response.data.error, "no se conecta");
      }
    }
  }
};
</script>
