<template>
  <div class="row">
    <div class="col-lg-4 col-sm-6 mb-4">
      <b-card
        title
        img-src
        img-alt="Image"
        img-top
        tag="article"
        style="max-width: 20rem;"
        class="mb-2"
      >
        <span>{{city}}Aqui va el nombre de la ciudad</span>
        <span>{{country}} Aqui el Pais</span>
        <b-button @click.prevent="showModal" href="#" variant="primary">More</b-button>
      </b-card>
    </div>
    <b-modal id="modal-1" size="xl" title="Nombre de la ciudad">
      <div class="container">
        <div class="row justify-content-center">
          <div class="col-lg-4">
            <div class="modal-body">
              <!-- Project Details Go Here-->
              <h2 class="text-uppercase">Project Name</h2>
              <img
                class="img-fluid d-block mx-auto"
                src="https://upload.wikimedia.org/wikipedia/commons/b/b6/Plaza_de_Espa%C3%B1a_%28Sevilla%29_-_01.jpg"
                alt
              />
              <span>Weather</span>
              <span>Humidity</span>
            </div>
          </div>
          <div class="col-lg-8">
            <div class="modal-body">
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
              <table class="table" id="table-2">
                <h3>Quality of life(score)</h3>
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
        </div>
      </div>
    </b-modal>
  </div>
</template>

<script>
export default {
  props: [
    "city",
    "region",
    "country",
    "currency",
    "population",
    "genderRatio",
    "weather",
    "humidity",
    "image",
    "segurity",
    "fun",
    "quealityHospitals",
    "friendlyForegeigners",
    "levelofEducation",
    "tolerance",
    "friendlyEnviromental",
    "jobOpportunities"
  ],
  data() {
    return {
      body: ""
      /*       cityCard:{
        city: "",
        region: "",
        country: "",
        currency: "",
        population: "",
        genderRatio: "",
        weather: "",
        humidity: "",
        image: "",
        segurity: "",
        fun: "",
        quealityHospitals: "",
        friendlyForegeigners: "",
        levelofEducation: "",
        tolerance: "",
        friendlyEnviromental: "",
        jobOpportunities: "",
      } */
    };
  },
  methods: {
    showModal() {
      this.$bvModal.show("modal-1");
    },
    hideModal() {
      this.$bvModal.hide("modal-1");
    }
  }
};
</script>
