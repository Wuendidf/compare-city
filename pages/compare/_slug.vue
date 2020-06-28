<template>
  <section class="compareCity">
    <div class="container">
      <table class="table table-responsive-sm">
        <thead>
          <tr>
            <th scope="col">Cost Of Living</th>
            <th scope="col" style="color:#ED5917" v-for="item in dataCityCosts" :key="item.id">{{item.cityName}}</th>
            <th scope="col">Percent%</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="key in costOfLivingKeys" :key="key.id">
            <th scope="row"><i class="em em-moneybag" aria-role="presentation" aria-label="MONEY BAG"></i>{{costOfLivingLabels[key]}}</th>
            <td >{{dataCityCosts[0].costOfLiving[key] | toMoney}}</td>
            <td>{{dataCityCosts[1].costOfLiving[key] | toMoney}}</td>
            <td
            :class="className(getPercent(dataCityCosts,key))"
            >{{getPercent(dataCityCosts,key)}}%</td>
          </tr>
          <tr>
          <b-col md="3" class="py-3">
            <b-button
              v-b-popover.hover="'The Consumer Price Index (CPI): is the annual variation of consumer prices with respect to the period 2020M04. INE'"
              title="Information"
              variant="success"
            >
              <i class="fas fa-info"></i>
            </b-button>
          </b-col>

          </tr>
        </tbody>
      </table>

      <div class="share">
        <div class="btn-fb">
          Share in
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
    </div>


  </section>
</template>

<script>
export default {
  data() {
    return {
      currentParams: this.$route.params.slug,
      dataCityCosts: [],
      costOfLivingKeys: [],
      costOfLivingLabels: {
        basicServices: "Basic services: electricity, water and gas",
        bread: "A loaf of bread (250g)",
        cocaCola: "Coca-Cola (0,33l)",
        coffee: "Coffee",
        consumerIndex: "Consumer Price Index",
        dinner: "Dinner for one person in a restaurant",
        gasoline: "Gasoline (1l)",
        internet: "Monthly internet rent",
        jeans: "A pair of blue jeans",
        mcDonalds: "McDonalds Standard Menu",
        rentCenter:
          "Monthly rental of a one-bedroom apartment in the city-center",
        rentCenterBig: "Monthly rental of a 3-bedroom apartment in the center",
        rentOutCenter:
          "Monthly rental of a one-bedroom apartment on the outskirts of the city",
        salary: "Minimum Salary",
        shoes: "A pair of Nike sneakers",
        transportation: "Monthly transport ticket",
        unemploymentRate: "Unemployment rate"
      },
    };
  },
  mounted() {
    this.getDataCityCosts();
  },
  methods: {
    async getDataCityCosts() {
      try {
        let response = await this.$axios.get(
          `https://comparecity.herokuapp.com/compare/${this.currentParams}`
        );

        this.dataCityCosts = response.data;
        this.costOfLivingKeys = Object.keys(this.dataCityCosts[0].costOfLiving);
      } catch (err) {
        console.log(err.message);
      }
    },
    getPercent(dataCityCosts, key) {

      let price1 = dataCityCosts[0].costOfLiving[key]
      let price2 = dataCityCosts[1].costOfLiving[key]

      let priceListMax = Math.max(price1, price2);
      let priceListMin = Math.min(price1, price2);
      let percent = Math.abs((priceListMax * 100) / priceListMin - 100).toFixed(
        1
      );
      if (price1 > price2) {
        percent = percent * -1;
      }
      return percent;
    },
    className(percent) {
      let percentType = Math.sign(percent);
        if (percentType === -1) {
          return "negative";
        }
        return "positive";
    }
  },
  computed: {

  }
};
</script>

<style scoped>
.negative {
  color: red;
  font-style: oblique;
  font-weight: bold
}
.positive {
  color: green;
  font-weight: bold
}

</style>
