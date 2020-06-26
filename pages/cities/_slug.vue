<template>
  <section class="page-section">
    <div class="container-fluid container-sm">
      <img class="img-fluid d-block mx-auto" src="#" alt />
      <div class="row justify-content-center">
        <div class="col-lg-12">
          <h2 class="card-title">{{ cityData.cityName }}Un cambio</h2>
        </div>
      </div>
      <div class="row justify-content-center">
        <div class="col-lg 5">
          <div role="tablist">
            <b-card no-body class="mb-1">
              <b-card-header header-tag="header" class="p-1" role="tab">
                <b-button block v-b-toggle.accordion-1 variant="info">
                  <h3 class="btn-info">
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
                    </svg>
                    Generals info
                  </h3>
                </b-button>
              </b-card-header>
              <b-collapse id="accordion-1" visible accordion="my-accordion" role="tabpanel">
                <b-card-body>
                  <table class="table" id="table-1">
                    <tbody>
                      <tr>
                        <th scope="row">
                          <i class="em em-world_map" aria-role="presentation" aria-label></i>
                          Region
                        </th>
                        <td scope="col">{{ cityData.region }}</td>
                      </tr>
                      <tr>
                        <th scope="row">
                          <i class="em em-cityscape" aria-role="presentation" aria-label></i>
                          Country
                        </th>
                        <td>{{ cityData.country }}</td>
                      </tr>
                      <tr>
                        <th scope="row">
                          <i
                            class="em em-currency_exchange"
                            aria-role="presentation"
                            aria-label="CURRENCY EXCHANGE"
                          ></i>
                          Currency
                        </th>
                        <td>{{ cityData.currency }}</td>
                      </tr>
                      <tr>
                        <th scope="row">
                          <i
                            class="em em-raising_hand"
                            aria-role="presentation"
                            aria-label="HAPPY PERSON RAISING ONE HAND"
                          ></i>Population
                        </th>
                        <td>{{ cityData.population }}</td>
                      </tr>
                      <tr>
                        <th scope="row">
                          <i class="em em-partly_sunny_rain" aria-role="presentation" aria-label></i>
                          Temperature
                        </th>
                        <td>
                          {{ cityData.weather }}ºC Average annual temperature and
                          <span
                            style="color:red"
                          >{{ temp }}ºC now</span>
                        </td>
                      </tr>
                      <tr>
                        <th scope="row">
                          <i class="em em-wind_blowing_face" aria-role="presentation" aria-label></i>Humidity
                        </th>
                        <td>
                          <span style="color:red">{{ humidity }}% now</span>
                        </td>
                      </tr>
                    </tbody>
                  </table>
                </b-card-body>
              </b-collapse>
            </b-card>
            <b-card no-body class="mb-1">
              <b-card-header header-tag="header" class="p-1" role="tab">
                <b-button block v-b-toggle.accordion-2 variant="info">
                  <h3 class="btn-info">
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
                    </svg>
                    Quality of life
                  </h3>
                </b-button>
              </b-card-header>
              <b-collapse id="accordion-2" visible accordion="my-accordion" role="tabpanel">
                <b-card-body>
                  <table class="table" id="table-2">
                    <tbody>
                      <tr>
                        <th scope="row">
                          <i class="em em-cop" aria-role="presentation" aria-label="POLICE OFFICER"></i>
                          Segurity
                        </th>
                        <td>
                          {{ cityData.segurity }}
                          <div class="progress">
                            <div
                              class="progress-bar 0"
                              role="progressbar"
                              :style="'width:' + cityData.segurity + ''"
                              aria-valuenow="25"
                              aria-valuemin="0"
                              aria-valuemax="100"
                            ></div>
                          </div>
                        </td>
                      </tr>
                      <tr>
                        <th scope="row">
                          <i
                            class="em em-partying_face"
                            aria-role="presentation"
                            aria-label="FACE WITH PARTY HORN AND PARTY HAT"
                          ></i>
                          Fun
                        </th>
                        <td>
                          {{ cityData.fun }}
                          <div class="progress">
                            <div
                              class="progress-bar"
                              role="progressbar"
                              :style="'width:' + cityData.fun + ''"
                              aria-valuenow="25"
                              aria-valuemin="0"
                              aria-valuemax="100"
                            ></div>
                          </div>
                        </td>
                      </tr>
                      <tr>
                        <th scope="row">
                          <i class="em em-hospital" aria-role="presentation" aria-label="HOSPITAL"></i>
                          Quality of hospitals
                        </th>
                        <td>
                          {{ cityData.qualityHospitals }}
                          <div class="progress">
                            <div
                              class="progress-bar"
                              role="progressbar"
                              :style="'width:' + cityData.qualityHospitals + ''"
                              aria-valuenow="25"
                              aria-valuemin="0"
                              aria-valuemax="100"
                            ></div>
                          </div>
                        </td>
                      </tr>
                      <tr>
                        <th scope="row">
                          <i
                            class="em em-two_men_holding_hands"
                            aria-role="presentation"
                            aria-label="TWO MEN HOLDING HANDS"
                          ></i>
                          Friendly to foreigners
                        </th>
                        <td>
                          {{ cityData.friendlyForegeigners }}
                          <div class="progress">
                            <div
                              class="progress-bar"
                              role="progressbar"
                              :style="'width:' + cityData.friendlyForegeigners + ''"
                              aria-valuenow="25"
                              aria-valuemin="0"
                              aria-valuemax="100"
                            ></div>
                          </div>
                        </td>
                      </tr>
                      <tr>
                        <th scope="row">
                          <i
                            class="em em-mortar_board"
                            aria-role="presentation"
                            aria-label="GRADUATION CAP"
                          ></i>Level of education
                        </th>
                        <td>
                          {{ cityData.levelofEducation }}
                          <div class="progress">
                            <div
                              class="progress-bar"
                              role="progressbar"
                              :style="'width:' + cityData.levelofEducation + ''"
                              aria-valuenow="25"
                              aria-valuemin="0"
                              aria-valuemax="100"
                            ></div>
                          </div>
                        </td>
                      </tr>
                      <tr>
                        <th scope="row">
                          <i
                            class="em em-handshake"
                            aria-role="presentation"
                            aria-label="HANDSHAKE"
                          ></i>
                          Tolerance (racial)
                        </th>
                        <td>
                          {{ cityData.tolerance }}
                          <div class="progress">
                            <div
                              class="progress-bar"
                              role="progressbar"
                              :style="'width:' + cityData.tolerance + ''"
                              aria-valuenow="25"
                              aria-valuemin="0"
                              aria-valuemax="100"
                            ></div>
                          </div>
                        </td>
                      </tr>
                      <tr>
                        <th scope="row">
                          <i
                            class="em em-recycle"
                            aria-role="presentation"
                            aria-label="BLACK UNIVERSAL RECYCLING SYMBOL"
                          ></i>
                          Friendly enviromental
                        </th>
                        <td>
                          {{ cityData.friendlyEnviromental }}
                          <div class="progress">
                            <div
                              class="progress-bar"
                              role="progressbar"
                              :style="'width:' + cityData.friendlyEnviromental + ''"
                              aria-valuenow="25"
                              aria-valuemin="0"
                              aria-valuemax="100"
                            ></div>
                          </div>
                        </td>
                      </tr>
                      <tr>
                        <th scope="row">
                          <i class="em em-female-office-worker" aria-role="presentation" aria-label></i>Job opportunities
                        </th>
                        <td>
                          {{ cityData.jobOpportunities }}
                          <div class="progress">
                            <div
                              class="progress-bar"
                              role="progressbar"
                              :style="'width:' + cityData.jobOpportunities + ''"
                              aria-valuenow="25"
                              aria-valuemin="0"
                              aria-valuemax="100"
                            ></div>
                          </div>
                        </td>
                      </tr>
                    </tbody>
                  </table>
                </b-card-body>
              </b-collapse>
            </b-card>
            <b-card no-body class="mb-1">
              <b-card-header header-tag="header" class="p-1" role="tab">
                <b-button block v-b-toggle.accordion-3 variant="info">
                  <h3 class="btn-info">
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
                    </svg>
                    Maps
                  </h3>
                </b-button>
              </b-card-header>
              <b-collapse id="accordion-3" visible accordion="my-accordion" role="tabpanel">
                <b-card-body>
                  <Maps
                    v-if="cityData.coordenadas"
                    :center="cityData.coordenadas"
                    :map-type-id="mapTypeId"
                    :zoom="5"
                  >aquii el componente</Maps>
                </b-card-body>
              </b-collapse>
            </b-card>
          </div>
          <b-card no-body class="mb-1">
            <b-card-header header-tag="header" class="p-1" role="tab">
              <b-button block v-b-toggle.accordion-4 variant="info">
                <h3 class="btn-info">
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
                  </svg>
                  Video
                </h3>
              </b-button>
            </b-card-header>
            <b-collapse id="accordion-4" visible accordion="my-accordion" role="tabpanel">
              <b-card-body>
                <youtube
                  :player-width="460"
                  :player-height="385"
                  position="relative"
                  class="video"
                  :video-id="cityData.videoId"
                ></youtube>
              </b-card-body>
            </b-collapse>
          </b-card>
        </div>

        <div class="row justify-content-center">
          <div class="col-lg 5">
            <div role="tablist"></div>
          </div>
        </div>
      </div>
      <div class="share">
        <div class="btn-fb">
          Share with your friends in
          <ShareNetwork
            network="facebook"
            url
            title="Say this comparison of cities."
            description="what do you think of this comparison"
            hashtags="CompareCity"
          >
            <i class="fab fa-facebook" style="color:blue"></i>
          </ShareNetwork>
        </div>
      </div>
      <div class="question" v-if="!hasVoted">
        <h3 class="text-secondary">If you have lived in this city, would you recommend it to live?</h3>
        <div class="container">
          <div class="row">
            <div class="col-lg 2">
              <button
                class="btn btn-primary btn-lg text-uppercase js-scroll-trigger"
                id="negative"
                @click.prevent="vote(voteNegative)"
              >
                <i class="far fa-thumbs-down"></i>
              </button>
            </div>
            <div class="col-lg 2">
              <button
                class="btn btn-primary btn-lg text-uppercase js-scroll-trigger"
                id="positive"
                @click.prevent="vote(votePositive)"
              >
                <i class="far fa-thumbs-up"></i>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import cityCard from "@/partials/CityCard";
import weather from "@/partials/weather";
import Maps from "@/components/Maps";
import Swal from "sweetalert2/dist/sweetalert2.js";

export default {
  data() {
    return {
      currentSlug: this.$route.params.slug,
      cityData: {},
      qualityOfLife: {},
      humidity: "",
      temp: "",
      center: {},
      mapTypeId: "terrain",
      markers: [{ position: { lat: -0.48585, lng: 117.1466 } }],
      votePositive: { votes: 1 },
      voteNegative: { votes: 0 },
      class: "",
      hasVoted: false
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
        this.cityData = response.data;
      } catch (err) {
        console.log(err.response.data.error, "no se conecta");
      }
    },
    async getWeather() {
      const token = "3408896f1d019f9845f9f0726d4dab41";
      const lang = "es";
      const unit = "metric";

      let URI = `https://api.openweathermap.org/data/2.5/weather?q=${this.cityData.cityName},es&appid=${token}&lang=${lang}&units=${unit}`;
      let response = await this.$axios.get(URI);

      this.humidity = response.data.main.humidity;
      this.temp = Math.trunc(response.data.main.temp);
    },
    async vote(data) {
      this.hasVoted = true
      try {
        let response = await this.$axios.put(
          `http://localhost:8082/votes/${this.currentSlug}`,
          data
        );

        console.log("has voted");
        Swal.fire({
          title: "Thanks for your vote, we will use it to improve our comparisons!",
          showClass: {
            popup: "animate__animated animate__fadeInDown"
          },
          hideClass: {
            popup: "animate__animated animate__fadeOutUp"
          }
        });
      } catch (err) {
        console.log(
          err.response.data.error,
          "no se conecta "
        );
      }
    }
  },
  computed: {},
  components: {
    Maps: Maps
  }
};
</script>

<style>
</style>
