<template>
  <div class="col-lg-4 col-sm-6 mb-4">
    <div class="portfolio-item" @click.prevent= "showCity">
      <a class="portfolio-link" data-toggle="modal" href="#">
        <div class="portfolio-hover">
          <div class="portfolio-hover-content"></div>
        </div>
        <img class="img-fluid" :src="image">
      </a>
      <div class="portfolio-caption">
        <div class="portfolio-caption-heading">{{cityName}}</div>
        <div class="portfolio-caption-subheading text-muted">{{country}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    "cityName",
    "country",
    "image",
    "slug",
  ],
  data() {
    return {
      body: ""
    };
  },
  methods: {
    showCity(item){
      this.$emit("click", item)
    },
  }
};
</script>
