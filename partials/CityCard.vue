<template>
  <div class="col-lg-4 col-sm-6 mb-4">
    <div class="card" @click.prevent="showCity">
      <a class="portfolio-link">
        <img class="card-img-top" :src="image" />
      </a>
      <h4 class="text-secondary">{{cityName}}</h4>
      <div class="portfolio-caption-subheading text-muted">{{country}}</div>
      <div class="portfolio-caption-subheading text-muted"><i class="far fa-thumbs-up" style="color:orange"></i>{{votes}}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["cityName", "country", "image", "slug", "votes"],
  data() {
    return {
      body: ""
    };
  },
  methods: {
    showCity(item) {
      this.$emit("click", item);
    }
  }
};
</script>
