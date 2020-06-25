<template>
  <div class="mainSlider" :class="size">
    <header class="masthead">
        <div class="masthead-subheading">let's explore together</div>
        <nuxt-link class="btn btn-primary btn-xl text-uppercase js-scroll-trigger" to="/cities">Get started!</nuxt-link>
    </header>
  </div>
</template>

<script>
export default {
  props: ["image", "size"]
};
</script>
