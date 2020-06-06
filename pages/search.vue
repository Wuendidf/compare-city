<template>
  <div class="search">
    <section class="page-section bg-light" id="search">
      <div class="container">
        <div class="row">
          <div class="col-lg-12 text-center">
            <h2 class="section-heading text-uppercase">Found your city</h2>
            <h3 class="section-subheading text-muted">Write the name here.</h3>
          </div>
          <div class="col-lg-12 text-center">
            <form class="form-inline">
              <input
                class="form-control mr-sm-2"
                type="text"
                placeholder="Search"
                aria-label="Search"
              />
              <button class="btn btn-outline-success my-2 my-sm-0" type="submit">go</button>
            </form>
          </div>
        </div>
        <CityCard :country=""></CityCard>
      </div>
    </section>
  </div>
</template>

<script>
import CityCard from "@/partials/CityCard";

export default {
  data() {
    return {
      cityCards:
        {
          city: "Madrid",
          region: "",
          country: "España"
          /*         currency: "",
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
        jobOpportunities: "", */
        }
    }
    },
  components: {
    CityCard
  }
};
</script>

