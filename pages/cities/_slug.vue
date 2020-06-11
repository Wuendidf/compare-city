<template>
  <section class="page-section bg-light">
    <div class="container">
      <img class="img-fluid d-block mx-auto" src="#" alt />
      <div class="row justify-content-center">
        <div class="col-lg-12">
          <h2 class="text-primary">{{cityData.cityName}}</h2>
        </div>
      </div>
      <div class="row justify-content-center">
        <div class="col-lg-6">
          <h3 class="text-secondary">
            <svg
              class="bi bi-check-circle-fill"
              width="1em"
              height="1em"
              viewBox="0 0 16 16"
              fill="currentColor"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill-rule="evenodd"
                d="M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0zm-3.97-3.03a.75.75 0 0 0-1.08.022L7.477 9.417 5.384 7.323a.75.75 0 0 0-1.06 1.06L6.97 11.03a.75.75 0 0 0 1.079-.02l3.992-4.99a.75.75 0 0 0-.01-1.05z"
              />
            </svg> Generals info
          </h3>
          <table class="table" id="table-1">
            <tbody>
              <tr>
                <th scope="row">Region</th>
                <td scope="col">{{cityData.region}}</td>
              </tr>
              <tr>
                <th scope="row">Country</th>
                <td>{{cityData.country}}</td>
              </tr>
              <tr>
                <th scope="row">Currency</th>
                <td>{{cityData.currency}}</td>
              </tr>
              <tr>
                <th scope="row">Population</th>
                <td>{{cityData.population}}</td>
              </tr>
              <tr>
                <th scope="row">Temperature</th>
                <td>{{cityData.weather}}ºC Average annual temperature and {{temp}}ºC now</td>
              </tr>
              <tr>
                <th scope="row">Humidity</th>
                <td>{{humidity}}% now</td>
              </tr>
            </tbody>
          </table>
        </div>
        <div class="col-lg-6">
          <h3 class="text-secondary">
            <svg
              class="bi bi-check-circle-fill"
              width="1em"
              height="1em"
              viewBox="0 0 16 16"
              fill="currentColor"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill-rule="evenodd"
                d="M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0zm-3.97-3.03a.75.75 0 0 0-1.08.022L7.477 9.417 5.384 7.323a.75.75 0 0 0-1.06 1.06L6.97 11.03a.75.75 0 0 0 1.079-.02l3.992-4.99a.75.75 0 0 0-.01-1.05z"
              />
            </svg> Quality of life
          </h3>
          <table class="table" id="table-2">
            <tbody>
              <tr>
                <th scope="row">Segurity</th>
                <td scope="col">{{cityData.segurity}}</td>
              </tr>
              <tr>
                <th scope="row">Fun</th>
                <td>{{cityData.fun}}</td>
              </tr>
              <tr>
                <th scope="row">Quality of hospitals</th>
                <td>{{cityData.qualityHospitals}}</td>
              </tr>
              <tr>
                <th scope="row">Friendly to foreigners</th>
                <td>{{cityData.friendlyForegeigners}}</td>
              </tr>
              <tr>
                <th scope="row">Level of education</th>
                <td>{{cityData.levelofEducation}}</td>
              </tr>
              <tr>
                <th scope="row">Tolerance (racial)</th>
                <td>{{cityData.tolerance}}</td>
              </tr>
              <tr>
                <th scope="row">Friendly enviromental</th>
                <td>{{cityData.friendlyEnviromental}}</td>
              </tr>
              <tr>
                <th scope="row">Job opportunities</th>
                <td>{{cityData.jobOpportunities}}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>

      <youtube class :video-id="cityData.videoId"></youtube>
    </div>
  </section>
</template>

<script>
import cityCard from "@/partials/CityCard";
import weather from "@/partials/weather"

export default {
  data() {
    return {
      currentSlug: this.$route.params.slug,
      cityData: {},
      humidity: "",
      temp:""
    };
  },
  mounted() {
    this.setDataCity();
    this.getWeather();
  },
  methods: {
    async setDataCity() {
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
    },
    async getWeather(){
      const token = "3408896f1d019f9845f9f0726d4dab41";
      const lang = "es";
      const unit = "metric";

      let URI = `https://api.openweathermap.org/data/2.5/weather?q=${this.cityData.cityName},es&appid=${token}&lang=${lang}&units=${unit}`;
      let response= await this.$axios.get(URI)
      console.log(response)

      this.humidity = response.data.main.humidity
      this.temp = Math.trunc(response.data.main.temp)
      console.log(humidity)
    }
  }
};
</script>
