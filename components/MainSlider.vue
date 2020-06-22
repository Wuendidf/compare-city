<template>
  <div class="MainSlider" :class="size">
    <header class="masthead">
      <div class="container">
        <div class="masthead-subheading">let's explore together</div>
        <a class="btn btn-primary btn-xl text-uppercase js-scroll-trigger" href="/cities">Get started!</a>
      </div>

    </header>
  </div>
</template>

<script>
export default {
  props: ["image", "size"]
};
</script>
