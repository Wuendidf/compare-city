<template>
  <section class="compareCity">
    <div class="container">
      <table class="table">
        <thead>
          <tr>
            <th scope="col">costOfLiving</th>
            <th scope="col" v-for="item in dataCityCosts" :key="item.id">{{item.cityName}}</th>
            <th scope="col">Percent%</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="key in costOfLivingKeys" :key="key.id">
            <th scope="row">{{costOfLivingLabels[key]}}</th>
            <td>{{dataCityCosts[0].costOfLiving[key] | toMoney}}</td>
            <td>{{dataCityCosts[1].costOfLiving[key] | toMoney}}</td>
            <td
             :class="changeClass"
            >{{getPercent(dataCityCosts[0].costOfLiving[key],dataCityCosts[1].costOfLiving[key])}}</td>

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
  props: {
    isType: Boolean
  },
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
      className: ""
    };
  },
  mounted() {
    this.getDataCityCosts();
  },
  methods: {
    async getDataCityCosts() {
      try {
        let response = await this.$axios.get(
          `http://localhost:8082/compare/${this.currentParams}`
        );

        this.dataCityCosts = response.data;
        this.costOfLivingKeys = Object.keys(this.dataCityCosts[0].costOfLiving);
        console.log(this.costOfLivingKeys);
      } catch (err) {
        console.log(err.message);
      }
    },
    getPercent(price1, price2) {
      let priceListMax = Math.max(price1, price2);
      let priceListMin = Math.min(price1, price2);
      let percent = Math.abs((priceListMax * 100) / priceListMin - 100).toFixed(1);
      if (price1 > price2) {
        percent = percent * -1;
      }
      let percentType = Math.sign(this.percent)
      if (percentType === -1){
        return  this.className = "negative"
        console.log(this.className)
      }
      else if (percentType === 1){
        return this.className = "positive"
      }
      return percent
    },

  },
  computed: {
    changeClass(percent) {
      let percentType = Math.sign(this.percent)
      if (percentType === -1){
        return  this.className = "negative"
        console.log(this.className)
      }
      else if (percentType === 1){
        return this.className = "positive"
      }

  }
  }
};
</script>

<style scoped>
.negative {
  color: red;
}
.positive {
  color: green;
}
</style>
